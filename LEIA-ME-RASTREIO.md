# Rastreio de cargas

A seção "Rastreio" do site lê o arquivo `rastreio.json`, na raiz do repositório.
Os códigos que estão nele hoje (`CAD123456`, `CAD654321`, `CAD111222`) são **exemplos**.

Por segurança, o rastreio mostra só **três etapas**: Coletado, Em trânsito e Entregue.
Ele **não mostra** cidade, rota, local atual da carga, volumes nem nomes de clientes.

## Como cadastrar ou atualizar uma carga

Edite `rastreio.json` (pode ser direto pelo GitHub, botão do lápis) e faça commit.
O site atualiza em cerca de 1 minuto.

```json
"CAD999888": {
  "coletado": "2026-10-08T09:00",
  "transito": null,
  "entregue": null,
  "previsao": "2026-10-12"
}
```

- A chave (`CAD999888`) é o código que o cliente digita. Use MAIÚSCULAS e sem espaços.
- A etapa atual é definida pelas datas preenchidas: só `coletado` = Coletado;
  `transito` preenchido = Em trânsito; `entregue` preenchido = Entregue.
  Use `null` nas etapas que ainda não aconteceram.
- `previsao` é opcional e some da tela depois que a carga é entregue.
- O arquivo inteiro é público (qualquer pessoa pode abrir `/rastreio.json`).
  Não coloque nele nenhuma informação que permita localizar a carga ou identificar o cliente.

## Limitação

Este modelo é estático (GitHub Pages não tem servidor). Alguém precisa atualizar o arquivo
a cada movimentação. Para rastreio automático, o site precisa consultar o sistema da Cadomar
(TMS/ERP) por uma API. Para isso, é preciso saber qual sistema é usado.

Códigos curtos ou previsíveis podem ser testados um a um por qualquer pessoa. Prefira
códigos longos e difíceis de adivinhar (por exemplo, 10 ou mais caracteres aleatórios).
