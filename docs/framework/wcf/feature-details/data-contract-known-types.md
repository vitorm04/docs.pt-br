---
title: Tipos de contratos de dados conhecidos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: dc297bd35d7bfdb25fc50135b8e684e1b9452cb2
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592576"
---
# <a name="data-contract-known-types"></a>Tipos de contratos de dados conhecidos
O <xref:System.Runtime.Serialization.KnownTypeAttribute> classe permite que você especificar, com antecedência, os tipos que devem ser incluídos para consideração durante a desserialização. Para obter um exemplo de funcionamento, consulte o [tipos conhecidos de](../../../../docs/framework/wcf/samples/known-types.md) exemplo.  
  
 Normalmente, ao passar parâmetros e valores retornados entre um cliente e um serviço, ambos os pontos de extremidade compartilham todos os contratos de dados dos dados a serem transmitidos. No entanto, isso não for o caso nas seguintes circunstâncias:  
  
- O contrato de dados enviados é derivado do contrato de dados esperado. Para obter mais informações, consulte a seção sobre a herança no [equivalência de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)). Nesse caso, os dados transmitidos não tem os mesmos dados conforme o esperado, o ponto de extremidade de recebimento do contrato.  
  
- O tipo declarado para obter as informações a serem transmitidos é uma interface, em vez de uma classe, estrutura ou enumeração. Portanto, ele não pode ser conhecido com antecedência qual tipo que implementa a interface, na verdade, é enviada e, portanto, o ponto de extremidade de recebimento não pode determinar antecipadamente o contrato de dados para os dados transmitidos.  
  
- O tipo declarado para obter as informações a serem transmitidos é <xref:System.Object>. Como cada tipo herda de <xref:System.Object>e ele não pode ser conhecido com antecedência qual tipo realmente é enviado, o ponto de extremidade de recebimento não pode determinar antecipadamente o contrato de dados para os dados transmitidos. Esse é um caso especial do primeiro item: Cada contrato de dados é derivado do padrão, um contrato de dados em branco que é gerado para <xref:System.Object>.  
  
- Alguns tipos, que incluem os tipos do .NET Framework, tem membros que estão em uma das três categorias acima. Por exemplo, <xref:System.Collections.Hashtable> usa <xref:System.Object> para armazenar os objetos reais na tabela de hash. Durante a serialização desses tipos, o lado de recebimento não pode determinar antecipadamente o contrato de dados para esses membros.  
  
## <a name="the-knowntypeattribute-class"></a>A classe KnownTypeAttribute  
 Quando os dados chegam a um ponto de extremidade de recebimento, o tempo de execução do WCF tenta desserializar os dados para uma instância de um tipo do common language runtime (CLR). O tipo que é instanciado para desserialização é escolhido pelo primeiro inspecionando a mensagem de entrada para determinar os dados de contrato para que o conteúdo da mensagem está em conformidade com. O mecanismo de desserialização, em seguida, tenta encontrar um tipo CLR que implementa um contrato de dados compatível com o conteúdo da mensagem. O conjunto de tipos de candidato que permite o mecanismo de desserialização durante esse processo é chamado como conjunto do desserializador de "tipos conhecidos".  
  
 Uma maneira de informar ao mecanismo de desserialização sobre um tipo é usando o <xref:System.Runtime.Serialization.KnownTypeAttribute>. O atributo não pode ser aplicado aos membros de dados individuais, somente a tipos de contrato de dados inteira. O atributo é aplicado a um *tipo externo* que pode ser uma classe ou estrutura. Durante o uso mais básico, aplicando o atributo especifica um tipo como um "tipo conhecido". Isso faz com que o tipo conhecido ser uma parte do conjunto de tipos conhecidos, sempre que um objeto do tipo externo ou qualquer objeto referenciado por meio de seus membros está sendo desserializado. Mais de um <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo pode ser aplicado para o mesmo tipo.  
  
## <a name="known-types-and-primitives"></a>Primitivos e tipos conhecidos  
 Tipos primitivos, bem como alguns tipos são tratados como primitivos (por exemplo, <xref:System.DateTime> e <xref:System.Xml.XmlElement>) são sempre "na conhecidos" e nunca devem ser adicionadas por meio desse mecanismo. No entanto, tem matrizes de tipos primitivos a serem adicionados explicitamente. A maioria das coleções são considerados equivalentes às matrizes. (Coleções não genéricas são consideradas equivalentes a matrizes de <xref:System.Object>). Para obter um exemplo da usando primitivos, matrizes primitivas e primitivas coleções, consulte o exemplo 4.  
  
> [!NOTE]
>  Ao contrário de outros tipos primitivos, o <xref:System.DateTimeOffset> estrutura não é um tipo conhecido por padrão, portanto, devem ser adicionada manualmente à lista de tipos conhecidos.  
  
## <a name="examples"></a>Exemplos  
 Os exemplos a seguir mostram o <xref:System.Runtime.Serialization.KnownTypeAttribute> classe em uso.  
  
#### <a name="example-1"></a>Exemplo 1  
 Há três classes com uma relação de herança.  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 O seguinte `CompanyLogo` classe pode ser serializada, mas não pode ser desserializado se o `ShapeOfLogo` membro é definido como um `CircleType` ou um `TriangleType` do objeto, porque o mecanismo de desserialização não reconhece nenhum tipo com nomes de contrato de dados " Círculo"ou"Triângulo".  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 A maneira correta de escrever o `CompanyLogo` tipo é mostrado no código a seguir.  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 Sempre que o tipo externo `CompanyLogo2` está sendo desserializado, o mecanismo de desserialização conhece `CircleType` e `TriangleType` e, portanto, é capaz de localizar tipos correspondentes para os contratos de dados do "Círculo" e "Triângulo".  
  
#### <a name="example-2"></a>Exemplo 2  
 No exemplo a seguir, mesmo que ambos `CustomerTypeA` e `CustomerTypeB` têm a `Customer` de contrato de dados, uma instância do `CustomerTypeB` é criado sempre que um `PurchaseOrder` é desserializado, pois apenas `CustomerTypeB` é conhecido para o mecanismo de desserialização.  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a>Exemplo 3:  
 No exemplo a seguir, uma <xref:System.Collections.Hashtable> armazena seu conteúdo internamente como <xref:System.Object>. Para desserializar com êxito uma tabela de hash, o mecanismo de desserialização deve saber o conjunto de tipos possíveis que podem ocorrer lá. Nesse caso, podemos saber com antecedência que somente `Book` e `Magazine` objetos são armazenados na `Catalog`, portanto, esses são adicionados usando o <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo.  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a>Exemplo 4  
 No exemplo a seguir, um contrato de dados armazena um número e uma operação para executar o número. O `Numbers` membro de dados pode ser um inteiro, uma matriz de inteiros, ou um <xref:System.Collections.Generic.List%601> que contém números inteiros.  
  
> [!CAUTION]
>  Isso só funcionará no lado do cliente se SVCUTIL. EXE é usado para gerar um proxy do WCF. SVCUTIL. EXE recupera os metadados do serviço, incluindo quaisquer tipos conhecidos. Sem essas informações um cliente não será capaz de desserializar os tipos.  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 Este é o código do aplicativo.  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a>Interfaces, herança e tipos conhecidos  
 Quando um tipo conhecido é associado a um tipo específico usando o `KnownTypeAttribute` atributo, o tipo conhecido também está associado a todos os tipos derivados desse tipo. Por exemplo, consulte o código a seguir.  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 O `DoubleDrawing` classe não exige o `KnownTypeAttribute` atributo para usar `Square` e `Circle` no `AdditionalShape` campo, pois a classe base (`Drawing`) já tenha esses atributos aplicados.  
  
 Tipos conhecidos podem ser associados apenas com classes e estruturas, interfaces não.  
  
## <a name="known-types-using-open-generic-methods"></a>Tipos conhecidos usando métodos genéricos abertos  
 Ele pode ser necessário adicionar um tipo genérico como um tipo conhecido. No entanto, um tipo genérico aberto não pode ser passado como um parâmetro para o `KnownTypeAttribute` atributo.  
  
 Esse problema pode ser resolvido por meio de um mecanismo alternativo: Escreva um método que retorna uma lista de tipos a serem adicionados à coleção de tipos conhecidos. O nome do método, em seguida, é especificado como um argumento de cadeia de caracteres para o `KnownTypeAttribute` atributo devido a algumas restrições.  
  
 O método deve existir no tipo ao qual o `KnownTypeAttribute` atributo é aplicado, deve ser estático, não deve aceitar nenhum parâmetro e deve retornar um objeto que pode ser atribuído a <xref:System.Collections.IEnumerable> de <xref:System.Type>.  
  
 Não é possível combinar as `KnownTypeAttribute` atributo com um nome de método e `KnownTypeAttribute` atributos com tipos reais no mesmo tipo. Além disso, você não pode aplicar mais de um `KnownTypeAttribute` com um nome de método para o mesmo tipo.  
  
 Consulte a classe a seguir.  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 O `theDrawing` campo contém instâncias de uma classe genérica `ColorDrawing` e uma classe genérica `BlackAndWhiteDrawing`, que herdam de uma classe genérica `Drawing`. Normalmente, ambos devem ser adicionadas aos tipos conhecidos, mas o código a seguir não é uma sintaxe válida para os atributos.  
  
```csharp  
// Invalid syntax for attributes:  
// [KnownType(typeof(ColorDrawing<T>))]  
// [KnownType(typeof(BlackAndWhiteDrawing<T>))]  
```  
  
```vb  
' Invalid syntax for attributes:  
' <KnownType(GetType(ColorDrawing(Of T))), _  
' KnownType(GetType(BlackAndWhiteDrawing(Of T)))>  
```  
  
 Portanto, um método deve ser criado para esses tipos de retorno. A maneira correta de escrever esse tipo, em seguida, é mostrada no código a seguir.  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a>Outras maneiras de adicionar tipos conhecidos  
 Além disso, os tipos conhecidos podem ser adicionados por meio de um arquivo de configuração. Isso é útil quando você não controlar o tipo que requer tipos conhecidos para desserialização apropriada, como quando usando produtos de terceiros com o Windows Communication Foundation (WCF) de bibliotecas de tipos.  
  
 O arquivo de configuração a seguir mostra como especificar um tipo conhecido em um arquivo de configuração.  
  
 `<configuration>`  
  
 `<system.runtime.serialization>`  
  
 `<dataContractSerializer>`  
  
 `<declaredTypes>`  
  
 `<add type="MyCompany.Library.Shape,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL">`  
  
 `<knownType type="MyCompany.Library.Circle,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL"/>`  
  
 `</add>`  
  
 `</declaredTypes>`  
  
 `</dataContractSerializer>`  
  
 `</system.runtime.serialization>`  
  
 `</configuration>`  
  
 Um tipo de contrato de dados chamado de arquivo na configuração anterior `MyCompany.Library.Shape` é declarado com `MyCompany.Library.Circle` como um tipo conhecido.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [Tipos conhecidos](../../../../docs/framework/wcf/samples/known-types.md)
- [Equivalência de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Criando contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md)
