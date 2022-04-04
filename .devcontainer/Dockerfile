FROM debian:bullseye

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Fix locales warnings
RUN apt-get -qq update \
    && apt-get -qq install locales \
    && echo "en_US.UTF-8 UTF-8" >>/etc/locale.gen \
    && locale-gen

# Create the user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    # Add sudo support.
    && apt-get -qq update \
    && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -qq install sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

RUN apt-get -qq update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -qq install wget curl gnupg2 locate \
    && apt-get -qq install git cmake build-essential bash-completion autoconf libtool \
    && apt-get -qq install gdb gperf strace
RUN updatedb

RUN apt-get -qq install ruby ruby-dev
RUN gem install bundler jekyll tzinfo tzinfo-data jekyll-theme-minimal

# RUN wget -nv -c https://raw.githubusercontent.com/STEllAR-GROUP/hpx/master/.clang-format -O /.clang-format \
#     && chmod a+r /.clang-format \
#     && wget -nv -c https://raw.githubusercontent.com/sharkdp/dbg-macro/master/dbg.h -O /usr/include/dbg.h \
#     && chmod a+r /usr/include/dbg.h

# # Add libstdc++ pretty printers for gdb to gdbinit
# RUN echo '\
# python\n\
# import sys\n\
# sys.path.insert(0, "/usr/share/gcc/python");\n\
# from libstdcxx.v6.printers import register_libstdcxx_printers;\n\
# register_libstdcxx_printers(None);\n\
# end\n\
# source /usr/share/gdb/auto-load/usr/lib/aarch64-linux-gnu/libstdc++.so.6.0.28-gdb.py\n\
# enable pretty-printer\n\
# ' >>/etc/gdb/gdbinit \
#     && chmod a+rw /etc/gdb/gdbinit

# Set default user
USER $USERNAME
SHELL ["/bin/bash"]
