Dynamic `allow`/`block` rules override static filtering rules.

There is a precedence logic for dynamic filtering cells:

Local rules override global rules.
- Local setting for `example.com` override global setting for `example.com`.

The party-specific cells override the type-specific cells.
- `3rd-party` override `images`
- `example.com` override `images`

The more specific the party, the higher the precedence.
- `example.com` overrides `3rd-party scripts`
- `www.example.com` overrides `example.com`

Party-specific, type specific cells override party-specific cells:
- `3rd-party frames` overrides `3rd-party`

All cells override the `all` cells. The local `all` cell overrides the global `all` cell.