# estudos_Swift

//
//  ContentView.swift
//  Estudos Swift
//
//  Created by Thierry Rizzo on 05/04/24.
//
func testeVariaveis (){
    let maximolog = 10
    // constante
    
    var logStarted = 0
    // variável. Aqui ele já definiu como int, se eu quisesse que fosse String, teria que por "0"
    
    var welcomeMessage: String = "Olá"
    // Aqui estou definindo que esta variavel é do tipo String
    
    welcomeMessage = "iai"
    
    var red, green, blue: Double
    // Aqui defini 3 variaveis de vez
    
    print(welcomeMessage)
    
    var teste = "saas"
    
    
    
    print(1.0, 2.0, 3.0, 4.0, 5.0, separator: " ... ")
    // Prints "1.0 ... 2.0 ... 3.0 ... 4.0 ... 5.0"
    
    for n in 1...5 {
        print(n, terminator: "")
    }
    // Prints "12345"
    
    
    print("O valor da variavel teste é: \(teste)")
    // Assim que funciona a interpolação de variáveis
    
}


// Tuplas

let codigoErro = (404,"Not found")
// Uma tupla guarda 2 ou mais valores que podem ser de tipos diferentes

let (numeroErro, mensagemErro) = codigoErro
let total = codigoErro
let (_ , apenasMensagem) = codigoErro

print ("O numero do erro é: '\(numeroErro)' e a mensagem de erro é: '\(mensagemErro)'") 

print ("Agora eu quero saber desse aqui: \(total), mas será q esse vai? \(apenasMensagem)")


print ("Indicando qual elemento da tupla eu quero exibir pelo indice: \(codigoErro.1)")
    


let codigoErro2 = (code: 200, description: "Ok")
print("O novo código é: '\(codigoErro2.code)' e a nova mensagem é: '\(codigoErro2.description)")




// Optionals

let possibleNumber = "123"
let convertedNumber = Int(possibleNumber)
print(convertedNumber)

// Se o possibleNumber fosse um texto tipo "Hello" o valor do convertedNumber seria "nil" ou seja, nulo

if convertedNumber != nil {
    print("ConvertedNumber tem algum valor inteiro")
}

if convertedNumber != nil {
    print("ConvertedNumber tem um valor inteiro de: \(convertedNumber!)")
}
//Este é o forced Unwrapping, o valor não vai mais aparecer em (). Mas é preciso tomar cuidado. Sempre faça a verificação para saber se é nil ou não, pois se for, seu codigo irá quebrar.





// Optional chaining
class Residence {
    var numberOfRooms = 1
}

class Person {
    var residence: Residence?
}
    
let joao = Person ()
    if let roomCount = joao.residence?.numberOfRooms {
        print("A residência do João tem \(roomCount) quartos")
        
    } else {
        print("Não foi possível recuperar o número de quartos.")
    }


joao.residence = Residence()

if let roomCount = joao.residence?.numberOfRooms {
    print("A residência do João tem \(roomCount) quartos")
} else {
    print("Não foi possível recuperar o número de quartos.")
}




let individualScores = [75, 43, 103, 87, 12]
var teamScore = 0
for score in individualScores {
    if score > 50 {
        teamScore += 3
    } else {
        teamScore += 1
    }
}
print(teamScore)


var optionalString: String? = "Olá"
print(optionalString == nil)
var optionalName: String? = "João de Santos"
var greeting = "Olá"
if let name = optionalName {
greeting = "Olá, \(name)"
}
let nickname:String? = nil
let fullName:String = "João de Deus"
let informalGreeting = "Oi \(nickname ?? fullName)"

// nesse caso, se eu printasse só o nickname, o compilador não aceita, pois o nickname é um optional e pode ser nil, então para resolver isso, usei um valor alternativo, no caso passei o fullname que é String normal. O uso das interrogações é para que se o nickname for nil, ele vai printar o fullname, mas nickname tiver um valor válido, apenas ele será printado. "é um ou outro"mas a preferência vai ser sempre do primeiro, no caso o nickname.


let vegetable = "pimentão vermelho"

switch vegetable {
case "salsão":
    print("Adicione algumas uvas passas")
case "pepino","agrião":
    print("Isso daria um bo sanduiche")
case let x where x.hasPrefix("pimentão"):
    print("É picante \(x)?")
default:
    print("Tudo vai bem na sopa!")
}

// No caso do let x, eu estou atribuindo a constante usada no switch a 'x', e estou verificando se o valor tem pimentão na frente.


var someInts: [Int] = []
//iniciando array vazio
print("Este array tem \(someInts.count) itens")
someInts.append(7)
print(someInts)

var threeDoubles = Array(repeating: 1.4, count: 5) 
print(threeDoubles)
var anotherThreeDoubles = Array(repeating: 2.5, count: 3) 
print(anotherThreeDoubles)
var allDoubles = threeDoubles + anotherThreeDoubles
print(allDoubles)

// É possivel juntar os valores de arrays em um só

allDoubles += [4]
print(allDoubles)
// Outra forma de adicionar itens num array


var shoppingList: [String] = ["Ovos","Leite"]
print("A lista de itens tem \(shoppingList.count) itens")

if shoppingList.isEmpty {
    print("A lista de compras está vazia.")
}
else {
    print("A lista de compras não está vazia")
}

shoppingList.append ("Farinha")
shoppingList += ["Fermento em pó"]



var firstItem = shoppingList[0]
shoppingList[0] = "Seis ovos"
// Atribuindo um valor a um indice especifico do array
print (shoppingList)

shoppingList[2...3] = ["Bananas", "Maçãs"] 
print (shoppingList)
shoppingList.insert ("Xarope de bordo", at: 0) 
// Aqui estamos adicionando um valor numa posição especifica, não substitui o valor anterior. Eles são passados para frente
print (shoppingList)
let mapleSyrup = shoppingList.remove(at: 0)
// Remove um especifico
print (shoppingList)
shoppingList.removeLast()
// remove o ultimo elemento
print (shoppingList)


for (index, value) in shoppingList.enumerated() {
    print("item \(index + 1): \(value)")
}


for item in shoppingList {
    print("item: \(item)")
}



// Mesmo principio de join no mysql
let oddDigits: Set = [1, 3, 5, 7, 9]
let evenDigits: Set = [0, 2, 4, 6, 8]
let singleDigitsPrimeNumber: Set = [2, 3, 5, 7]
oddDigits.union(evenDigits).sorted()
//Union junta todos. Junta A e B totalmente
oddDigits.intersection(evenDigits).sorted()
//O que faz parte dos dois. Intersseção de A e B
oddDigits.subtracting(singleDigitsPrimeNumber).sorted()
//O que faz parte apenas da sobra do A, ignorando a interseção e o resto do lado B
oddDigits.symmetricDifference(singleDigitsPrimeNumber).sorted()
//Retira a intersseção e deixa apenas as sobras dos lados A e B





var nomeNumeros: [Int : String] = [:]
//Isso é um dicionário. Iniciei ele vazio
nomeNumeros [16] = "Dezesseis"

var airPoint: [String : String] = ["SSA": "Salvador", "DUB": "Dublin", "GRU": "Guarulhos"]

airPoint["LHR"]="London"
// Assim adiciona



func saudacao(person:String, day:String) -> String {
    // O que vem depois da seta é o tipo do retorno
    return ("Olá, \(person), hoje é \(day)")
}

print(saudacao(person: "Jorge", day: "terça feira"))


func calculateStatistics(scores: [Int]) -> (min: Int, max: Int, sum: Int) {
    // Nesse caso o tipo de retorno é uma tupla
    var min = scores[0]
    var max = scores[0]
    var sum = 0
    
    for score in scores {
        if score > max {
            max = score
        } else if score < min {
            min = score
        }
        
        sum += score
    }
    return (min, max, sum)
}

calculateStatistics(scores: [5,3,100,3,9])
print(calculateStatistics(scores: [5,3,100,3,9]))





// Closures ({})
var numbers = [20, 19, 7, 12]
numbers.map({ (number: Int) -> Int in
            // Primeiro o parâmetro e o tipo de retorno, depois do in é o próprio bloco que deseja fazer
  let restul = 3 * number
  return restul
})


let mappedNumbers = numbers.map({ number in 3 * number })
print(mappedNumbers)

let sortedNumbers = numbers.sorted { $0 > $1 }
print(sortedNumbers)
// Organizando do maior para o menor




func fetchUsername(from server: String) async -> String {
    let userId = await fetchUserId(from: server)
    if userId == 501 {
        return "João Souza"
    }
        return "Convidado"
    }
}
// Assim vc define uma função como async. Ela pode ser executada em paralelo com outras

func connectUser(to server: String) async {
    async let userId = fetchUserId(from: server).     
    async let username = fetchUsername (from: server)
    // Nesse caso, como essas duas constantes só estão recebendo o valor de funções asyncs, eu também coloquei elas como async, pois não preciso que elas recebam esses valores em uma ordem específica.
    let greeting = await "Olá \(username), user ID \(userId)"
    // Nesse caso, como estou USANDO esses valores, preciso esperar que as funções sejam executadas para aí sim usar os valores.
    print (greeting)
}

Task {
    await connectUser(to: "Primary")
}
// Para chamar as funções async usamos Task


func send(job: Int, toPrinter printerName: String) throws -> String {
    // Usa o throws no inicio da função quando ela pode retornar um erro
    if printerName = "Não possui toner" {
        throw PrinterError.noToner
        // Usa throw para mandar um erro
    }
    return "Trabalho enviado"
}




// O guard é como se fosse o if, mas não tem necessidade de alinhamento e é importante pois garante que todas as condições sejam atendidas antes de executar o codigo principal.
func lerECalcularInvestimento() {
    guard let valorInicialStr = readLine(), let valorInicial = Double(valorInicialStr),
          let taxaJurosStr = readLine(), let taxaJuros = Double(taxaJurosStr),
          let periodoStr = readLine(), let periodo = Int(periodoStr) else {
        print("Entrada inválida!")
        return
    }
    
    let valorFinal = valorInicial * pow(1 + taxaJuros, Double(periodo))
    print(String(format: "Valor final do investimento: R$ %.2f", valorFinal))
}

lerECalcularInvestimento()





// Essa função retorna um tipo genérico. Item Não é uma String ou Int, ele não existe, ele vai ser determinado de acordo com a entrada.
func makeArray<Item>(repeating item: Item, numberOfTimes: Int) -> [Item] {
var result: [Item] = []
    for _ in 0..<numberOfTimes {
        result.append(item)
    }
return result
}
makeArray (repeating: "bater", numberOfTimes: 4)
