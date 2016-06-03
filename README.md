# Build Instructions

```
$ corebuild io.native
```

# Example Usage

```
$ _build/io.native io.ml
open Core.Std

(* let main () = *)
(*  let file_str = In_channel.read_all filename in *)
(*    print_string file_str *)

let print_file file =
  let file_str = In_channel.read_all file in
    print_string file_str

let spec =
  let open Command.Spec in
  empty
  +> anon ("filename" %: string)

let command =
  Command.basic
    ~summary:"Takes a file and outputs that file as a string"
    ~readme:(fun () -> "More detailed information")
    spec
    (fun filename () -> print_file filename)

let () =
  Command.run ~version:"1.0" ~build_info:"RWO" command
```