# Site CCHLA-UFRN — Tema WordPress

Projeto de customização do tema institucional do CCHLA-UFRN, mantido pela Gerência de Redes do CCHLA-UFRN.

## Estrutura

- `tema-original/` — submódulo com o tema base da Agência Web (IFRN). **Referência, não editar.** Fica sincronizado com o upstream `awe-zn/CCHLA-UFRN` (branch `wp-thema`).
- `tema-cchla/` — cópia editável do tema. **É aqui que o trabalho acontece.** Vira o tema `cchla-ufrn` dentro do WordPress.
- `docker-compose.yml` — ambiente local (WordPress + MariaDB + Adminer).

## Rodar localmente

Requer Docker Desktop aberto.

```bash
docker compose up -d
```

Serviços:

- Site: http://localhost:8080
- Admin: http://localhost:8080/wp-admin
- Adminer (banco): http://localhost:8081 — servidor `db`, usuário `wordpress`, senha `wordpress`, base `wordpress`

### Primeiro acesso

1. Abra http://localhost:8080 e conclua o instalador do WordPress (título, usuário admin, senha).
2. Em `Aparência → Temas`, ative **CCHLA UFRN**.
3. Configure links permanentes em `Configurações → Links Permanentes → Nome do post` (necessário pros post types do tema: cursos, departamentos, publicações, etc.).

Editar qualquer arquivo em `tema-cchla/` reflete no site na hora (bind mount).

### Parar / resetar

```bash
docker compose down        # para os containers (mantém os dados)
docker compose down -v     # apaga tudo, incluindo o banco (recomeça do zero)
```

## Atualizar o tema base (referência)

```bash
git submodule update --remote tema-original
```

Depois compare com `tema-cchla/` para trazer o que fizer sentido.
