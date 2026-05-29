class Animal:
    def __init__(self, id_animal, especie, raca, peso, status_saude="Saudável"):
        self.id_animal = id_animal
        self.especie = especie
        self.raca = raca
        self.peso = peso
        self.status_saude = status_saude

    def exibir_info(self):
        return f"[Animal] ID: {self.id_animal} | Espécie: {self.especie} | Raça: {self.raca} | Peso: {self.peso}kg | Saúde: {self.status_saude}"


class Lavoura:
    def __init__(self, cultura, area_hectares, data_plantio, status="Em crescimento"):
        self.cultura = cultura
        self.area_hectares = area_hectares
        self.data_plantio = data_plantio
        self.status = status

    def exibir_info(self):
        return f"[Lavoura] Cultura: {self.cultura} | Área: {self.area_hectares} ha | Plantio: {self.data_plantio} | Status: {self.status}"


class Fazenda:
    def __init__(self, nome):
        self.nome = nome
        self.rebanho = []
        self.lavouras = []

    def adicionar_animal(self, animal):
        self.rebanho.append(animal)
        print(f"✅ Animal {animal.id_animal} adicionado ao rebanho.")

    def adicionar_lavoura(self, lavoura):
        self.lavouras.append(lavoura)
        print(f"🌱 Lavoura de {lavoura.cultura} registrada com sucesso.")

    def gerar_relatorio_geral(self):
        print(f"\n--- RELATÓRIO GERAL DA FAZENDA {self.nome.upper()} ---")
        
        print("\n🔹 Setor de Pecuária:")
        if not self.rebanho:
            print("Nenhum animal cadastrado.")
        for animal in self.rebanho:
            print(animal.exibir_info())

        print("\n🔹 Setor de Agricultura:")
        if not self.lavouras:
            print("Nenhuma lavoura cadastrada.")
        for lavoura in self.lavouras:
            print(lavoura.exibir_info())
        print("-" * 40)


# --- Demonstração do Sistema ---
if __name__ == "__main__":
    # Inicializando a fazenda
    minha_fazenda = Fazenda("Terra Viva")

    # Cadastrando Animais (Pecuária)
    animal1 = Animal(id_animal="G001", especie="Bovino", raca="Nelore", peso=450)
    animal2 = Animal(id_animal="G002", especie="Bovino", raca="Angus", peso=480, status_saude="Em tratamento")
    minha_fazenda.adicionar_animal(animal1)
    minha_fazenda.adicionar_animal(animal2)

    # Cadastrando Lavouras (Agricultura)
    lavoura1 = Lavoura(cultura="Soja", area_hectares=150, data_plantio="12/10/2025")
    lavoura2 = Lavoura(cultura="Milho", area_hectares=80, data_plantio="05/01/2026", status="Pronto para colheita")
    minha_fazenda.adicionar_lavoura(lavoura1)
    minha_fazenda.adicionar_lavoura(lavoura2)

    # Gerando o relatório na tela
    minha_fazenda.gerar_relatorio_geral()
