# Módulo para cadastro, filtragem e análise estatística de preços de produtos.

def gerenciar_produtos():
    # Inicializa uma lista vazia para armazenar os dicionários de produtos
    produtos = []
    
    print("=== Cadastro de Produtos (Digite 'sair' no nome para encerrar) ===")
    
    while True:
        nome = input("Nome do produto: ").strip()
        
        if nome.lower() == "sair":
            break
            
        if not nome:
            print("O nome do produto não pode ser vazio.")
            continue
            
        try:
            preco = float(input(f"Preço de '{nome}' (R$): "))
            if preco < 0:
                print("O preço não pode ser negativo.")
                continue
        except ValueError:
            print("Por favor, digite um valor numérico válido para o preço.")
            continue
            
        categoria = input(f"Categoria de '{nome}': ").strip().capitalize()
        if not categoria:
            categoria = "Sem Categoria"
            
        # Adiciona o produto na lista usando o método append() solicitado
        produtos.append({
            "nome": nome,
            "preco": preco,
            "categoria": categoria
        })

    if not produtos:
        print("Nenhum produto foi cadastrado.")
        return

    print("\n--- Filtragem de Produtos ---")
    try:
        valor_corte = float(input("Digite um valor de preço para filtrar (R$): "))
        tipo_filtro = input("Deseja listar produtos 'acima' ou 'abaixo' deste valor? ").strip().lower()
        
        print(f"\nProdutos com valor {tipo_filtro} de R$ {valor_corte:.2f}:")
        encontrou_filtro = False
        
        for prod in produtos:
            if tipo_filtro == "acima" and prod["preco"] > valor_corte:
                print(f" • {prod['nome']} - R$ {prod['preco']:.2f} [{prod['categoria']}]")
                encontrou_filtro = True
            elif tipo_filtro == "abaixo" and prod["preco"] < valor_corte:
                print(f" • {prod['nome']} - R$ {prod['preco']:.2f} [{prod['categoria']}]")
                encontrou_filtro = True
                
        if not encontrou_filtro:
            print(" Nenhum produto atendeu ao critério de filtragem.")
    except ValueError:
        print("Valor de corte inválido. Pulando etapa de filtragem.")

    # Ordenação crescente usando obrigatoriamente .sort()
    produtos_crescente = produtos.copy()
    produtos_crescente.sort(key=lambda x: x["preco"])
    
    # Ordenação decrescente usando sorted(..., reverse=True)
    produtos_decrescente = sorted(produtos, key=lambda x: x["preco"], reverse=True)

    # Criar um set() para remover duplicatas das categorias
    categorias_unicas = set(prod["categoria"] for prod in produtos)

    # Tupla imutável com min(), max() e média
    lista_precos = [prod["preco"] for prod in produtos]
    estatisticas = (min(lista_precos), max(lista_precos), sum(lista_precos) / len(lista_precos))

    # Relatório formatado obrigatoriamente com f-strings
    print("\n" + "="*50)
    print("                RELATÓRIO DE PRODUTOS             ")
    print("="*50)
    
    print("Produtos por ordem Crescente de Preço (.sort()):")
    for prod in produtos_crescente:
        print(f" - {prod['nome']}: R$ {prod['preco']:.2f} ({prod['categoria']})")
        
    print("\nProdutos por ordem Decrescente de Preço (sorted()):")
    for prod in produtos_decrescente:
        print(f" - {prod['nome']}: R$ {prod['preco']:.2f} ({prod['categoria']})")
        
    print(f"\nConjunto de Categorias Únicas (set): {categorias_unicas}")
    
    print("\nEstatísticas Gerais (Tupla):")
    # Acessando os valores da tupla por seus respectivos índices, [1] e [2]
    print(f" • Menor Preço: R$ {estatisticas[0]:.2f}")
    print(f" • Maior Preço: R$ {estatisticas[1]:.2f}")
    print(f" • Média dos Preços: R$ {estatisticas[2]:.2f}")
    print("="*50)

# Executa a função principal do Python
if __name__ == "__main__":
    gerenciar_produtos()



# VERSÃO EQUIVALENTE EM PORTUGOL 
# programa
# {
#     funcao inicio()
#     {
#         // Uso de vetores de tamanho fixo (Capacidade máxima: 100 itens)
#         cadeia nomes[100]
#         real precos[100]
#         cadeia categorias[100]
#         inteiro total_produtos = 0
#         cadeia nome_input
#         
#         escreva("=== Cadastro de Produtos (Digite 'sair' no nome para encerrar) ===\n")
#         
#         // Laço de repetição condicional limitado ao tamanho máximo do vetor
#         enquanto (total_produtos < 100) {
#             escreva("Nome do produto: ")
#             leia(nome_input)
#             
#             se (nome_input == "sair" ou nome_input == "SAIR") {
#                 pare
#             }
#             
#             se (nome_input == "") {
#                 escreva("O nome do produto não pode ser vazio.\n")
#             } senao {
#                 nomes[total_produtos] = nome_input
#                 
#                 escreva("Preço de '", nomes[total_produtos], "' (R$): ")
#                 leia(precos[total_produtos])
#                 
#                 se (precos[total_produtos] < 0) {
#                     escreva("O preço não pode ser negativo.\n")
#                 } senao {
#                     escreva("Categoria de '", nomes[total_produtos], "': ")
#                     leia(categorias[total_produtos])
#                     
#                     se (categorias[total_produtos] == "") {
#                         categorias[total_produtos] = "Sem Categoria"
#                     }
#                     
#                     total_produtos = total_produtos + 1
#                 }
#             }
#         }
#
#         se (total_produtos == 0) {
#             escreva("Nenhum produto foi cadastrado.\n")
#             retorne
#         }
#
#         // --- FILTRAGEM POR PREÇO ---
#         real valor_corte
#         cadeia tipo_filtro
#         logico encontrou_filtro = falso
#         
#         escreva("\n--- Filtragem de Produtos ---\n")
#         escreva("Digite um valor de preço para filtrar (R$): ")
#         leia(valor_corte)
#         escreva("Deseja listar produtos 'acima' ou 'abaixo' deste valor? ")
#         leia(tipo_filtro)
#         
#         para (inteiro i = 0; i < total_produtos; i++) {
#             se (tipo_filtro == "acima" e precos[i] > valor_corte) {
#                 escreva(" • ", nomes[i], " - R$ ", precos[i], " [", categorias[i], "]\n")
#                 encontrou_filtro = verdadeiro
#             }
#             senao se (tipo_filtro == "abaixo" e precos[i] < valor_corte) {
#                 escreva(" • ", nomes[i], " - R$ ", precos[i], " [", categorias[i], "]\n")
#                 encontrou_filtro = verdadeiro
#             }
#         }
#
#         // --- ORDENAÇÃO PELO MÉTODO DA BOLHA (BUBBLE SORT) ---
#         cadeia nomes_cres[100]
#         real precos_cres[100]
#         cadeia categorias_cres[100]
#         
#         para (inteiro i = 0; i < total_produtos; i++) {
#             nomes_cres[i] = nomes[i]
#             precos_cres[i] = precos[i]
#             categorias_cres[i] = categorias[i]
#         }
#         
#         para (inteiro i = 0; i < total_produtos - 1; i++) {
#             para (inteiro j = 0; j < total_produtos - i - 1; j++) {
#                 se (precos_cres[j] > precos_cres[j+1]) {
#                     real temp_preco = precos_cres[j]
#                     precos_cres[j] = precos_cres[j+1]
#                     precos_cres[j+1] = temp_preco
#                     
#                     cadeia temp_nome = nomes_cres[j]
#                     nomes_cres[j] = nomes_cres[j+1]
#                     nomes_cres[j+1] = temp_nome
#                     
#                     cadeia temp_cat = categorias_cres[j]
#                     categorias_cres[j] = categorias_cres[j+1]
#                     categorias_cres[j+1] = temp_cat
#                 }
#             }
#         }
#
#         // --- SIMULAÇÃO MANUAL DE CONJUNTO (CATEGORIAS ÚNICAS) ---
#         cadeia categorias_unicas[100]
#         inteiro total_unicas = 0
#         
#         para (inteiro i = 0; i < total_produtos; i++) {
#             logico repetido = falso
#             para (inteiro j = 0; j < total_unicas; j++) {
#                 se (categorias[i] == categorias_unicas[j]) {
#                     repetido = verdadeiro
#                     pare
#                 }
#             }
#             se (nao repetido) {
#                 categorias_unicas[total_unicas] = categorias[i]
#                 total_unicas = total_unicas + 1
#             }
#         }
#
#         // --- ESTATÍSTICAS MANUAIS (MIN, MAX, MÉDIA) ---
#         real menor_preco = precos[0]
#         real maior_preco = precos[0]
#         real soma_precos = 0.0
#         
#         para (inteiro i = 0; i < total_produtos; i++) {
#             se (precos[i] < menor_preco) {
#                 menor_preco = precos[i]
#             }
#             se (precos[i] > maior_preco) {
#                 maior_preco = precos[i]
#             }
#             soma_precos = soma_precos + precos[i]
#         }
#         real media_precos = soma_precos / total_produtos
#     }
# }
