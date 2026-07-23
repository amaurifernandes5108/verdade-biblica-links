# verdade-biblica-links 🔗

**Hub de redirects (a "Ilha") do ecossistema Verdade Bíblica.** Cada vídeo longo do canal ganha um atalho curto e permanente que leva direto pra ele no YouTube. As legendas do Instagram e do TikTok apontam pros atalhos — a bio nunca mais precisa mudar.

## 🧭 Como funciona

Este projeto é servido pela **Vercel**. O arquivo `vercel.json` contém uma lista de redirects. Cada entrada transforma um caminho curto (ex: `/7tipos`) num link do YouTube.

Depois do deploy na Vercel, os atalhos ficam assim (troque pelo domínio real do projeto):

- `https://<seu-projeto>.vercel.app/7tipos` → vídeo "7 Tipos de Pessoas que Deus Manda Você Evitar"
- `https://<seu-projeto>.vercel.app/pare-de-ajudar` → vídeo "PARE DE AJUDAR quem Deus mandou parar"
- `https://<seu-projeto>.vercel.app/` (raiz) → página do canal

## ➕ Como adicionar um novo vídeo (o passo que se repete)

1. Abra o arquivo `vercel.json`.
2. Copie um bloco de redirect existente e cole antes do bloco da raiz (`/`).
3. Troque o `source` pelo atalho novo (ex: `/perdao`) e o `destination` pelo link exato do vídeo no YouTube.
4. Faça o commit. A Vercel republica sozinha em segundos.

Exemplo de bloco:

```json
{
  "source": "/perdao",
  "destination": "https://www.youtube.com/watch?v=SEU_ID_AQUI",
  "permanent": false
}
```

## ⚠️ Pendência (trocar quando tiver os links exatos)

Hoje os destinos de `/7tipos` e `/pare-de-ajudar` apontam provisoriamente para a **página do canal**. Assim que os links exatos dos dois vídeos estiverem em mãos, basta editar o `destination` de cada bloco no `vercel.json` para o URL do vídeo específico (`https://www.youtube.com/watch?v=...`). Isso faz a ponte cair direto no vídeo prometido pela legenda — conversão máxima.

## 🔒 Notas

- `"permanent": false` = redirect 302 (temporário). Use enquanto os destinos ainda podem mudar. Depois de estáveis, dá pra trocar para `true` (301, melhor para SEO), mas 302 é o mais seguro por ora.
- A bio do Instagram deve apontar para a **raiz** do hub ou para o canal — fixa, nunca mais muda. Cada legenda usa o atalho específico do vídeo.

---
*Infraestrutura de distribuição — estratégia da Ilha: YouTube é o destino, Instagram e TikTok são as pontes.*
