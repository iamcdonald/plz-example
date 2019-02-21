new_http_archive(
    name = "cpputest-archive",
    urls = [ "https://github.com/cpputest/cpputest/releases/download/v3.8/cpputest-3.8.zip" ],
    build_file = "./BUILD"
)

genrule(
  name = "cpputest-build",
  cmd = "cd $(location :cpputest-archive)/cpputest-3.8/cpputest_build && \
         ../configure && \
         make && \
         make check",
  outs = ["."],
  deps = [":cpputest-archive"]
)

cc_library(
  name = "cpputest",
  linker_flags = ["$(location :cpputest-build)/cpputest_build/lib"],
  hdrs = ["$(location :cpputest-build)/include"],
  deps = [":cpputest-build"]
)
