<!-- Roteiro comandos projeto -->
Instalar o uv

# 1. pipx (se você ainda não tem)
python -m pip install --user pipx
python -m pipx ensurepath

# 2. uv
pipx install uv

Criar o projeto

# 1. criar a pasta e entrar nela
mkdir olist
cd olist

# 2. iniciar o projeto (cria o pyproject.toml)
uv init --bare
<!-- --bare. Sem ele, o uv init monta um projeto empacotável: cria uma pasta src/ e uma seção [build-system] no pyproject.toml. Aí todo uv run passa a tentar construir o projeto antes de rodar — e como nosso código vai morar em pipeline/, e não em src/, ele falha com um erro de build que não tem nada a ver com o que você escreveu. O --bare cria só o pyproject.toml e mais nada -->

# 3. as bibliotecas do curso
uv add duckdb
<!-- uv add pandas streamlit -->
uv add --dev pytest ruff
<!-- O ambiente (.venv) e o uv.lock nascem no primeiro uv add — e, se você não tiver a versão de Python exigida, o próprio uv baixa. Quem clonar seu projeto depois roda uv sync e recebe exatamente as mesmas versões. Daqui para frente, todo comando começa com uv run. -->
