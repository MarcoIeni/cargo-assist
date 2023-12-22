# cargo-fmt-bot

Remember the old days when `cargo fmt --check` failed in CI and you had to run `cargo fmt && git commit -m "format" && git push` manually?
Well, those days are over, because the `cargo-fmt-bot` GitHub action does it for you!

Add the cargo-fmt-bot workflow file under the `.github/workflows` directory. For example `.github/workflows/cargo-fmt-bot.yml`:

```yaml
name: Cargo fmt bot

permissions:
  contents: write

on:
  push:

jobs:
  cargo-fmt-bot:
    name: Cargo fmt bot
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4
      - name: Install Rust toolchain
        uses: dtolnay/rust-toolchain@stable
      - name: Run Cargo fmt bot
        uses: MarcoIeni/cargo-fmt-bot@v0.1
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

<br>

<sup>
Licensed under either of <a href="LICENSE-APACHE">Apache License, Version 2.0</a>
or <a href="LICENSE-MIT">MIT license</a> at your option.
</sup>

<br>

<sub>
Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.
</sub>
