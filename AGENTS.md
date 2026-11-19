# Specs for Code.org software

This repo holds specs. It holds no application code; the code a spec
describes lives in another repo, named by the spec. Read `README.md` for how
the repo is used.

## Target repos

Most specs here target one or more of these. All are under the
`code-dot-org` GitHub organization and are usually checked out side by side
with this repo. Use the name exactly as written when a spec names its
target.

| Repo | Base branch | Holds |
|---|---|---|
| `code-dot-org` | `staging` | the product monorepo: Rails backend in `dashboard/`, React frontend in `apps/` and `frontend/`, the app's Helm chart in `k8s/helm` |
| `infrastructure` | `main` | infrastructure-as-code that is not part of the product: AWS accounts and CloudFormation stacks, observability, operational scripts |
| `k8s-gitops` | `main` | the GitOps repo for the Kubernetes cluster that runs the product; ArgoCD deploys what is merged to `main` |

A spec may target a repo not listed here. A change that spans repos, such
as a Helm chart edit in `code-dot-org` with a deployment edit in
`k8s-gitops`, is one spec that names both.

Each repo has its own `AGENTS.md`. Read it before changing that repo.

## Two tracks

- `openspec/` is managed by OpenSpec. Create, validate and archive changes
  with the OpenSpec skills and CLI. Do not edit anything under
  `openspec/changes/archive/`.
- `freeform/` holds plain markdown specs. Each file starts with the
  `status`, `owner` and `repos` fields described in `README.md`. Any
  structure below them is the author's choice; do not impose one.

Each spec is written in one place: either `openspec/` or `freeform/`, not
both. Do not copy a spec from one directory into the other, or convert one,
unless the user asks.

## Writing a spec

- Name the target repo or repos.
- State behavior a reader can check: what happens, to whom, under what
  condition. Leave out implementation detail the code will make obvious.
- Write plainly and exactly, for a competent engineer who does not know the
  subsystem. Define a term the first time it appears.
- Record open questions as open questions. Do not fill a gap with a guess.
- When the work changes direction, change the spec. A spec that disagrees
  with what is being built is wrong.

## Implementing from a spec

The target repo's `AGENTS.md` governs the code; this file governs the spec.
