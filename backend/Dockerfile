# 1. Imagen oficial de Python con versión fija (nunca latest)
FROM python:3.12-slim

# 2. Directorio de trabajo
WORKDIR /app

# 3. Evitar que Python genere archivos .pyc y forzar logs inmediatos
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# 4. Copiar e instalar dependencias
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# 5. Copiar el código de la aplicación
COPY app.py .

# 6. Indicar el puerto en el que corre la API
EXPOSE 8000

# 7. Arrancar con gunicorn en todas las interfaces (0.0.0.0) y puerto 8000
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "--workers", "2", "app:app"]