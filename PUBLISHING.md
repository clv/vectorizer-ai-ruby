# Publishing

RubyGems package: `vectorizer_ai`

Publishing uses RubyGems Trusted Publishing from GitHub Actions. Configure a trusted publisher in RubyGems with:

- Repository owner: `clv`
- Repository name: `vectorizer-ai-ruby`
- Workflow filename: `publish.yml`
- Environment name: `rubygems`

After that, push a SemVer tag such as `v1.0.0`. The workflow builds and publishes the gem through OIDC, then creates a GitHub release containing the `.gem` file.
