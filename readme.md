customized vim.lsp for my personal needs only


the official vim.lsp not fits my need well, but thanks to the flexiblity of lua to make these possible:

1) i added some extra functionlities:
* snippet support based on haolian9/parrot
* handler.goto supports splitting, removing duplicate results
* popup menu support
* processes management: ls, record idleness, expire idles, restart
* client.commands

2) and monkey-patched it:
* lsp.start treat {client,config}.root_dir=nil circum as 'single file mode', to reuse clients
* human-readable lsp.buf.rename, but removed multi-client support
* lsp.util.open_float_preview
    * no eye-candy (syntax/style)
    * 'land'-able and landed floatwins wont be closed automatically
* handlers.{sign,hover}: trimed '```', blank lines
* diagnostic.setloclist to comply with haolian9/sting.nvim
* fuzzy-matching on pre-vim.fn.complete() phase
* removed change.kind={create,delete} support in lsp.util.apply_workspace_edit
    * as it's has no checking on these changes which may cause security risks, eg: `rm -rf $HOME`
    * some lang servers may run on the net
    * some lang servers works like a proxy/forward server
    * there could be bug in a lang server


## prerequisites:
* neovim 0.10.*
* haolian9/infra.nvim
* haolian9/parrot.nvim
* haolian9/sting.nvim
* haolian9/beckon.nvim
* haolian9/puff.nvim


## config
due to its heavy dependency and personal purpose, it's not recommended to use it by others
but i think it's still worth to share it, hopping some can draw some inspiration from it.
