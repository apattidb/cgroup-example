MEM = """A=(); for i in `seq 5000000`; do A+=("a") ; done; echo "$${A[@]}" | wc -c """

genrule(
    name = "src",
    outs = ["mem.sh"],
    cmd = "echo '{}' > $@".format(MEM.replace("'", "'\\''")),
)

sh_test(
    name = "no-tag",
    srcs = [":src"],
)

sh_test(
    name = "tag-high",
    srcs = [":src"],
    tags = ["resources:memory:2000"]
)

sh_test(
    name = "tag-low",
    srcs = [":src"],
    tags = ["resources:memory:700"]
)
