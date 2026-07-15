# TechFlow Solutions - Sistema de Gerenciamento de Tarefas

## Objetivo
Sistema de gerenciamento de tarefas baseado em metodologias ágeis, desenvolvido para a startup de logística LogFlow. Permite acompanhar fluxo de trabalho em tempo real, priorizar tarefas críticas e monitorar desempenho da equipe.

## Escopo
- CRUD completo de tarefas
- Sistema de priorização de tarefas
- Anexo de arquivos às tarefas
- Testes automatizados
- Integração contínua com GitHub Actions
- **Monitoramento Robusto**: Logs estruturados, métricas Prometheus, dashboard Flask-MonitoringDashboard, health checks e rate limiting

## Metodologia
Desenvolvimento ágil com metodologia Kanban, utilizando GitHub Projects para organizar tarefas nas colunas "A Fazer", "Em Progresso" e "Concluído".

## Estrutura de Diretórios
- `/src`: Código fonte da aplicação
- `/tests`: Testes automatizados
- `/docs`: Documentação adicional
- `/.github/workflows`: Configurações de pipelines CI/CD
- `/logs`: Arquivos de log gerados automaticamente
- `/uploads`: Arquivos anexados às tarefas

## Como Executar

### Pré-requisito: Configurar o host 'techflow'
Para acessar http://techflow:5000, adicione a seguinte linha no arquivo `C:\Windows\System32\drivers\etc\hosts`:
```
127.0.0.1 techflow
```
Você precisa abrir o Bloco de Notas como Administrador para editar esse arquivo!

### Opção 1: Usando start.bat (Windows)
1. Clique duas vezes em `start.bat` ou execute via terminal:
   ```cmd
   start.bat
   ```
   Isso automaticamente cria um ambiente virtual, instala dependências e inicia o servidor!

### Opção 2: Manual
1. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```
2. Execute a aplicação:
   ```bash
   python src/app.py
   ```

## Recursos de Monitoramento Robusto

### 1. Dashboard de Monitoramento (`/dashboard`)
Acesse http://techflow:5000/dashboard para visualizar:
- Uso de memória e CPU
- Latência das requisições
- Número de requisições por endpoint
- Distribuição de status HTTP

### 2. Métricas Prometheus (`/metrics`)
Endpoint com métricas em formato Prometheus para integração com ferramentas como Grafana:
- Total de requisições HTTP (por método, endpoint e status code)
- Latência das requisições
- Uso de memória e CPU da aplicação
- Contagem de tarefas por status

### 3. Health Check (`/health`)
Endpoint para verificar o status da aplicação:
```json
{
  "status": "healthy",
  "memory_usage": 12345678,
  "cpu_usage": 15.5,
  "task_count": 42
}
```

### 4. Logs Estruturados
Logs em formato JSON, salvos em `/logs/app.log` e exibidos no console:
- Timestamp
- Nível de log (INFO, WARNING, ERROR)
- Mensagem detalhada
- Módulo, função e número da linha

### 5. Rate Limiting
Limitação de taxa para proteger a API:
- Padrão: 200 requisições/dia e 50/hora por IP
- GET /tasks: 100/minuto
- POST/PUT/DELETE: 50/minuto
- POST /tasks/{id}/attachments: 20/minuto

## Histórico de Commits
- Commits semânticos seguindo a convenção: `tipo(escopo): descrição`

## Controle de Qualidade
- Testes unitários com pytest
- Pipeline CI/CD configurado com GitHub Actions

## Mudança de Escopo (Simulação)
- Feature adicionada: Anexo de arquivos às tarefas
- Justificativa: Cliente solicitou capacidade de anexar documentos relevantes às tarefas (ex.: guias de remessa, relatórios de entrega)

## URLs de Acesso
- API Principal: http://techflow:5000
- Dashboard de Monitoramento: http://techflow:5000/dashboard
- Health Check: http://techflow:5000/health
- Métricas Prometheus: http://techflow:5000/metrics
