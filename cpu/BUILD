CPU = """PIDS=(); for i in `seq $$(nproc)`; do bash -c 'for i in `seq 200000`; do echo $$(( 2 ** 10 )); done' & PIDS+=($$!); done; for pid in "$${PIDS[@]}"; do wait $$pid; done"""

genrule(
    name = "src",
    outs = ["cpu.sh"],
    cmd = "echo '{}' > $@".format(CPU.replace("'", "'\\''")),
)

sh_test(
    name = "no-tag",
    srcs = [":src"],
)

sh_test(
    name = "tag-high",
    srcs = [":src"],
    tags = ["resources:cpu:8"]
)

sh_test(
    name = "tag-low",
    srcs = [":src"],
    tags = ["resources:cpu:1"]
)
