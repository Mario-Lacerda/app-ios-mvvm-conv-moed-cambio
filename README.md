# Desafio Dio - **Criando um aplicativo iOS no padrão MVVM para conversão de moedas e câmbio**



O padrão MVVM (Model-View-ViewModel) é um padrão de design amplamente utilizado em desenvolvimento de aplicativos iOS. Ele separa a lógica da interface do usuário (IU) da lógica de negócios, tornando o código mais fácil de manter e testar. Neste tutorial, criaremos um aplicativo iOS no padrão MVVM para conversão de moedas e câmbio.



## **Pré-requisitos**

- Xcode 13 ou superior
- Conhecimento básico de Swift e desenvolvimento iOS



### **Passo 1: Criar o projeto**

- Abra o Xcode e crie um novo projeto.
- Selecione "Aplicativo de exibição única".
- Nomeie o projeto como "CurrencyConverter".



### **Passo 2: Configurar o MVVM**

- Crie um novo grupo chamado "MVVM".

- Dentro do grupo "MVVM", crie os seguintes arquivos:

  a -  CurrencyConverterViewModel.swift (ViewModel)

  b - CurrencyConverterView.swift (View)



### **Passo 3: Criar o ViewModel**

- No arquivo `CurrencyConverterViewModel.swift`, defina a classe `CurrencyConverterViewModel`:

swift



```swift
import Foundation

class CurrencyConverterViewModel: ObservableObject {
    @Published var amount: Double = 0.0
    @Published var fromCurrency: String = "USD"
    @Published var toCurrency: String = "BRL"
    @Published var convertedAmount: Double = 0.0
    
    func convert() {
        // Lógica de conversão de moeda aqui
    }
}
```



**Passo 4: Criar a View**

- No arquivo `CurrencyConverterView.swift`, defina a classe `CurrencyConverterView`:

swift



```swift
import SwiftUI

struct CurrencyConverterView: View {
    @ObservedObject var viewModel: CurrencyConverterViewModel
    
    var body: some View {
        VStack {
            TextField("Valor", value: $viewModel.amount, formatter: NumberFormatter())
                .keyboardType(.decimalPad)
            Picker("Moeda de origem", selection: $viewModel.fromCurrency) {
                ForEach(["USD", "BRL"], id: \.self) {
                    Text($0)
                }
            }
            Picker("Moeda de destino", selection: $viewModel.toCurrency) {
                ForEach(["USD", "BRL"], id: \.self) {
                    Text($0)
                }
            }
            Button("Converter") {
                viewModel.convert()
            }
            Text("Valor convertido: \(viewModel.convertedAmount, specifier: "%.2f")")
        }
        .padding()
    }
}
```



**Passo 5: Conectar a View e o ViewModel**

- No arquivo `ContentView.swift`, substitua o conteúdo existente pelo seguinte:

swift



```swift
import SwiftUI

struct ContentView: View {
    @StateObject var viewModel = CurrencyConverterViewModel()
    
    var body: some View {
        CurrencyConverterView(viewModel: viewModel)
    }
}
```



**Passo 6: Executar o aplicativo**

- Execute o aplicativo no simulador ou dispositivo.

- Insira um valor na caixa de texto "Valor".

- Selecione as moedas de origem e destino nos seletores.

- Clique no botão "Converter" para converter o valor.

  

## **Conclusão**

Crie com sucesso um aplicativo iOS no padrão MVVM para conversão de moedas e câmbio. Este aplicativo demonstra os conceitos básicos do MVVM e pode ser estendido para incluir recursos adicionais, como suporte a várias moedas e taxas de câmbio em tempo real.

Como se faz um projeto completo para Criando um App iOS no Padrão MVVM para a Conversão de Moedas e Câmbio e colocar no github.



### **Projeto completo para criar um aplicativo iOS no padrão MVVM para conversão de moedas e câmbio e colocá-lo no GitHub:**

https://github.com/dio/formacao-swift-ios-experience/tree/main/projeto-3-moedas



### **Este projeto é composto pelos seguintes arquivos:**

- `AppCoordinator.swift`: Este arquivo define o coordenador de aplicativo responsável por gerenciar as telas do aplicativo.

  

- `CurrencyConverterViewModel.swift`: Este arquivo define a classe ViewModel que é responsável por gerenciar o estado do aplicativo.

  

- `CurrencyConverterView.swift`: Este arquivo define a tela de conversão de moedas.

- 

- `RatesService.swift`: Este arquivo define a classe Service que é responsável por obter as taxas de câmbio atuais.

- 

- `SceneDelegate.swift`: Este arquivo define o SceneDelegate que é responsável por gerenciar as janelas do aplicativo.

- 

- `ViewController.swift`: Este arquivo define a tela inicial do aplicativo.



Para criar este projeto, você precisará ter o Xcode instalado no seu computador. Você também precisará criar um novo projeto no Xcode. Depois de criar o projeto, você pode adicionar os arquivos do projeto fornecidos ao seu projeto.

Depois de adicionar os arquivos do projeto,  configurar o projeto. 

Para fazer isso,  precisa configurar o Target do seu projeto para usar o SwiftUI e o Swift Package Manager.  configurar o Serviço de Taxas para usar a API do ExchangeRatesAPI.

Depois de configurar o projeto, compilar e executar o aplicativo. 

O aplicativo deve exibir uma tela inicial que permite selecionar uma moeda de origem e uma moeda de destino. 

Pode selecionar a data e a hora para obter as taxas de câmbio atuais. Depois de selecionar as opções desejadas,  clicar no botão "Converter" para converter o valor de uma moeda para outra.

Este é apenas um projeto básico para criar um aplicativo iOS no padrão MVVM para conversão de moedas e câmbio. Você pode adicionar mais recursos ao aplicativo, como suporte a várias moedas e conversões de moedas offline.
