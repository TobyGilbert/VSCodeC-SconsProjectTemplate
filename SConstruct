import os.path

PROJECTNAME = "app"

DEBUG = ARGUMENTS.get("debug", 0)

PLATFORM = Platform()

# incldue path
ENV = Environment(CPPPATH=[".", "include", "/usr/local/include"])

ENV.Append(CCFLAGS="-std=c++17")
ENV.SConsignFile(os.path.join(ENV.Dir("#").abspath, ".sconsign.dblite"))

if int(DEBUG):
    ENV.Append(CCFLAGS="-ggdb3")

SOURCES = []
SOURCES = SOURCES + Glob("src/*.cpp")

LIBPATH = []
LIBPATH.append("/usr/local/lib")

LIBS = []

LINKFLAGS = []

if PLATFORM.name == "darwin":
    LINKFLAGS.extend(["-Wl", "-framework", "OpenGL", "-framework",
                      "Cocoa", "-framework", "IOKit", "-framework", "CoreVideo"])

elif PLATFORM.name == "win32":
    LINKFLAGS = LINKFLAGS

PROGRAM = ENV.Program(target="bin/" + PROJECTNAME + ".out", source=SOURCES,
                      libpath=LIBPATH, libs=LIBS, linkflags=LINKFLAGS)
