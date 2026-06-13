
import requests
import json

def buscar_dados(ip):
    print(f"Buscando informações para o IP: {ip}...")
    try:
        url = f"http://ip-api.com/json/{ip}"
        resposta = requests.get(url)
        dados = resposta.json()
        
        if dados['status'] == 'success':
            print("\n--- DADOS ENCONTRADOS ---")
            print(f"País: {dados['country']}")
            print(f"Região: {dados['regionName']}")
            print(f"Cidade: {dados['city']}")
            print(f"Provedor: {dados['isp']}")
            print("-------------------------\n")
        else:
            print("Não foi possível encontrar dados para este IP.")
    except Exception as e:
        print(f"Erro na conexão: {e}")

if __name__ == "__main__":
    alvo = input("Digite o IP que deseja consultar: ")
    buscar_dados(alvo)
