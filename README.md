# OpenSID `.github` — Reusable Workflows

Repo khusus organisasi untuk workflow yang dipakai ulang semua modul.

## Release Modul (IonCube + gh CLI)

- File: `actions/release-modul-action.yml`
- Dipakai via:
  ```yaml
  jobs:
    rilis:
      uses: OpenSID/.github/actions/release-modul-action.yml@main
      with:
        version: ${{ inputs.version || github.ref_name }}
        prerelease: ${{ inputs.prerelease || contains(github.ref_name, '-') }}
        encode_dirs: 'Config Http Models Providers Routes Services'
      secrets:
        IONCUBE_DOWNLOAD_URL: ${{ secrets.IONCUBE_DOWNLOAD_URL }}
  ```
- Contoh lengkap: `contoh/release.yml`
- Secret wajib di repo modul: `IONCUBE_DOWNLOAD_URL`
- Rilis dibuat murni dengan `gh` CLI (`gh release create/upload/edit/view`), tanpa `softprops/action-gh-release`.
- `Database/`, `Views/`, `Storage/` (dan `Resources/` untuk dtsen) sengaja tetap plain.
