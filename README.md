# inyecci-n-de-SQL-en-python
código en Python que simula el proceso de encontrar y corregir una vulnerabilidad conocida en un sistema. 
import re

# Simulación de una función vulnerable que usa SQL sin sanear
def vulnerable_function(input_data):
    query = "SELECT * FROM users WHERE username='" + input_data + "';"
    # Simulación de ejecución de la consulta y obtención de resultados
    return execute_query(query)

# Función para corregir la vulnerabilidad utilizando escapado de caracteres
def safe_function(input_data):
    # Escapar caracteres peligrosos
    sanitized_input = re.sub(r'[\'"\\]', r'\\\g<0>', input_data)
    query = "SELECT * FROM users WHERE username='" + sanitized_input + "';"
    # Simulación de ejecución de la consulta y obtención de resultados
    return execute_query(query)

# Función simulada para ejecutar una consulta SQL en la base de datos
def execute_query(query):
    # Simulación de ejecución de consulta y obtención de resultados
    results = [("user1", "password1"), ("user2", "password2")]
    return [row for row in results if query in row]

# Datos de entrada maliciosos
malicious_input = "' OR '1'='1"

print("Vulnerable function:")
vulnerable_results = vulnerable_function(malicious_input)
print("Results:", vulnerable_results)

print("\nSafe function:")
safe_results = safe_function(malicious_input)
print("Results:", safe_results)
