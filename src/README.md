# Atividades Extracurriculares da Escola Mergington

Site para consultar as atividades extracurriculares da Escola Mergington. Professores podem entrar no sistema para inscrever ou remover alunos das atividades.

## O que o site oferece

- Lista de atividades com descrição, horários, participantes e vagas disponíveis.
- Busca por nome, descrição ou horário, além de filtros por categoria, dia e período.
- Acesso de professores para inscrever alunos e removê-los de uma atividade.

## Executar localmente

O projeto usa Python, FastAPI e MongoDB. É necessário ter o MongoDB em execução em `mongodb://localhost:27017/`.

Na pasta principal do repositório, instale as dependências e inicie o servidor:

```bash
python -m pip install -r src/requirements.txt
python -m uvicorn src.app:app --reload
```

Abra <http://localhost:8000> para acessar o site. A documentação interativa da API fica em <http://localhost:8000/docs>, e a versão alternativa em <http://localhost:8000/redoc>.

## API

| Método | Rota | Descrição |
| --- | --- | --- |
| `GET` | `/activities/` | Lista atividades. Aceita filtros opcionais `day`, `start_time` e `end_time`. |
| `GET` | `/activities/days` | Lista os dias com atividades. |
| `POST` | `/auth/login` | Autentica um professor usando os parâmetros `username` e `password`. |
| `GET` | `/auth/check-session?username=...` | Confere se o professor existe. |
| `POST` | `/activities/{activity_name}/signup?email=...&teacher_username=...` | Inscreve um aluno; requer um professor válido. |
| `POST` | `/activities/{activity_name}/unregister?email=...&teacher_username=...` | Remove um aluno; requer um professor válido. |

Os dados são armazenados no MongoDB. Ao iniciar, o aplicativo adiciona atividades e contas de professores de exemplo somente quando as coleções correspondentes estão vazias.

## Mais informações

Consulte o [Guia de Desenvolvimento](../docs/how-to-develop.md) para detalhes adicionais sobre o ambiente de desenvolvimento.
