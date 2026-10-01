# Rastreio de cargas

A seção "Rastreio" do site lê o arquivo `rastreio.json`, na raiz do repositório.
Os códigos que estão nele hoje (`CAD123456`, `CAD654321`, `CAD111222`) são **exemplos**.

## Como cadastrar ou atualizar uma carga

Edite `rastreio.json` (pode ser direto pelo GitHub, botão do lápis) e faça commit.
O site atualiza em cerca de 1 minuto.

```json
"CAD999888": {
  "origem": "Canoas / RS",
  "destino": "Curitiba / PR",
  "servico": "Transporte de cargas",
  "volumes": "8 volumes",
  "previsao": "2026-10-10",
  "etapa": 2,
  "eventos": [
    { "data": "2026-10-08T09:00", "local": "Canoas / RS", "descricao": "Carga coletada na origem" }
  ]
}
```

- A chave (`CAD999888`) é o código que o cliente digita. Use MAIÚSCULAS e sem espaços.
- `etapa`: 1 = Coletada, 2 = Em trânsito, 3 = Saiu para entrega, 4 = Entregue.
- `eventos`: um item por atualização. O mais recente aparece primeiro, em qualquer ordem.
- Cada cliente consegue ver apenas o código que digitar, mas **o arquivo inteiro é público**
  (qualquer pessoa pode abrir `/rastreio.json`). Não coloque nomes, CNPJ, valores ou
  endereços de clientes nele.

## Limitação

Este modelo é estático (GitHub Pages não tem servidor). Alguém precisa atualizar o arquivo
a cada movimentação. Para rastreio automático, o site precisa consultar o sistema da Cadomar
(TMS/ERP) por uma API. Para isso, é preciso saber qual sistema é usado.
