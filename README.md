# spike-cargo-make

This is a test to see if we can use `cargo make` with common/shared task scripts to control our repository build/test/publish workflows both outside of nix and within nix.

I published a common cargo make toml file as a github gist here: https://gist.githubusercontent.com/neonphog/f034944d6960f72f2e1cb18c2961457b/raw

Obviously we'd want to do that as part of a repo or something instead of a gist, but this was quick.

The [Makefile.toml](./Makefile.toml) file in this repo, is just a small script to download that common one.

## Basically

After cloning this repo, you can just:

- `cargo install cargo-make` - to install cargo make
- `cargo make` - to run the full default 'version/check_fmt/clippy/test'
- or you can run the sub-tasks individually

## `cargo make` Considerations

- There is indeed a github action for cargo make - https://github.com/marketplace/actions/rust-cargo-make (I haven't tried it)
- Cross platform is still a little rough around the edges - the docs promote both duckscript and shell2batch for windows, neither of which are very comprehensive, but:
  - It does support good platform "conditions" so we can easily just manually write separate windows powershell scripts if it comes to that.
  - Or, it supports "rust" scripts, that compile rust binaries and runs them : )
