# Report template

Write the report in Brazilian Portuguese. Leave code, paths, identifiers
and quoted messages untouched. Omit a section that would be empty, except
Cobertura, which always appears.

```markdown
## Revisão: <alvo — ex.: branch feat/x contra origin/main, commit abc1234>

**Cobertura:** N arquivos alterados · R revisados · S pulados · E excluídos pelo ocr

### Crítico / Alto

- **`path/to/file.ts:42`** [bug] — O que está errado, numa frase.
  - **Cenário:** entrada ou estado concreto → resultado errado.
  - **Correção:** o que mudar.

### Médio

- **`path/to/file.ts:88`** [portabilidade] — …
  - **Cenário:** …
  - **Não verificado:** o que dependeria de ambiente/versão (se houver).

### Baixo

- **`path/to/file.ts:12`** [estilo] — … (só se valer a leitura)

### Perguntas

- **`path/to/file.ts:30`** — Algo sem cenário de falha único (contrato,
  manutenção, teste ausente) que merece resposta do autor.

### Mudanças de comportamento

- **Fluxo afetado:** antes → agora. Local: `path:linha`. Intencional ou não.

### Fora da revisão

- `path` — pulado: motivo concreto
- `path` — excluído pelo ocr: `default_path`

Descartados na verificação: K (motivo resumido, ex.: "guard em `x.ts:10`").
```

When nothing survives: "Nenhum problema crítico, alto ou médio em R
arquivos revisados", but only when Cobertura shows every changed file
either reviewed or explicitly out of scope.

Category labels (Portuguese in the report): bug, segurança, desempenho,
portabilidade, contrato, teste, manutenção, documentação, estilo.
