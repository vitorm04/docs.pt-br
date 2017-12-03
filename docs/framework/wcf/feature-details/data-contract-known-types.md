---
title: Tipos de contratos de dados conhecidos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cdb9e539d16b874ffd37b8e381757594561386e7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="data-contract-known-types"></a>Tipos de contratos de dados conhecidos
O <xref:System.Runtime.Serialization.KnownTypeAttribute> classe permite que você especificar com antecedência, os tipos que devem ser incluídos para consideração durante a desserialização. Para obter um exemplo de funcionamento, consulte o [tipos conhecidos](../../../../docs/framework/wcf/samples/known-types.md) exemplo.  
  
 Normalmente, ao passar parâmetros e valores de retorno entre um cliente e um serviço, ambos os pontos de extremidade compartilham todos os contratos de dados dos dados a serem transmitidos. No entanto, isso não for o caso nas seguintes circunstâncias:  
  
-   O contrato de dados enviados é derivado do contrato de dados esperado. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]a seção sobre a herança em [equivalência de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)). Nesse caso, os dados transmitidos não tem os mesmos dados conforme o esperado pelo ponto de extremidade de recebimento do contrato.  
  
-   O tipo declarado para as informações a serem transmitidos é uma interface, em vez de uma classe, estrutura ou enumeração. Portanto, ele não pode ser conhecido com antecedência qual o tipo que implementa a interface é enviada e, portanto, o ponto de extremidade de recebimento não pode determinar antecipadamente o contrato de dados para os dados transmitidos.  
  
-   O tipo declarado para as informações a serem transmitidos é <xref:System.Object>. Como cada tipo herda de <xref:System.Object>e ele não pode ser conhecido com antecedência qual tipo é realmente enviado, o ponto de extremidade de recebimento não pode determinar antecipadamente o contrato de dados para os dados transmitidos. Esse é um caso especial do primeiro item: cada contrato de dados é derivado do padrão, um contrato de dados em branco que é gerado para <xref:System.Object>.  
  
-   Alguns tipos, que incluem [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos, têm membros que estão em uma das três categorias a anterior. Por exemplo, <xref:System.Collections.Hashtable> usa <xref:System.Object> para armazenar os objetos reais na tabela de hash. Ao serializar desses tipos, o lado de recebimento não pode determinar antecipadamente o contrato de dados para esses membros.  
  
## <a name="the-knowntypeattribute-class"></a>A classe KnownTypeAttribute  
 Quando os dados chegam a um ponto de extremidade de recebimento, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tempo de execução tenta desserializar os dados em uma instância de um tipo do common language runtime (CLR). O tipo é instanciado para desserialização é escolhido inspecionando primeiro contrato que o conteúdo da mensagem está de acordo com a mensagem de entrada para determinar os dados. O mecanismo de desserialização, em seguida, tenta encontrar um tipo CLR que implementa um contrato de dados compatível com o conteúdo da mensagem. O conjunto de tipos de candidato que permite que o mecanismo de desserialização para durante esse processo é chamado de conjunto do desserializador de "tipos conhecidos".  
  
 Uma maneira de permitir que o mecanismo de desserialização saibam sobre um tipo é usando o <xref:System.Runtime.Serialization.KnownTypeAttribute>. O atributo não pode ser aplicado a membros de dados individuais, somente aos tipos de contrato de dados inteiro. O atributo é aplicado a um *tipo externo* que pode ser uma classe ou estrutura. Em seu uso mais básico, aplicando o atributo especifica um tipo como um "tipo conhecido". Isso faz com que o tipo conhecido ser parte do conjunto de tipos conhecidos sempre que um objeto do tipo externo ou qualquer objeto referenciado por meio de seus membros está sendo desserializado. Mais de um <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo pode ser aplicado para o mesmo tipo.  
  
## <a name="known-types-and-primitives"></a>Tipos primitivos e tipos conhecidos  
 Tipos primitivos, bem como alguns tipos são tratadas como tipos primitivos (por exemplo, <xref:System.DateTime> e <xref:System.Xml.XmlElement>) são sempre "é conhecido" e nunca devem ser adicionados por meio desse mecanismo. No entanto, matrizes de tipos primitivos precisam ser adicionados explicitamente. A maioria das coleções são consideradas equivalentes às matrizes. (Coleções não genéricas são consideradas equivalentes a matrizes de <xref:System.Object>). Para obter um exemplo de como o usar tipos primitivos, matrizes primitivas e coleções primitivo, consulte o exemplo 4.  
  
> [!NOTE]
>  Ao contrário de outros tipos primitivos, de <xref:System.DateTimeOffset> estrutura não é um tipo conhecido por padrão, portanto, devem ser adicionada manualmente à lista de tipos conhecidos.  
  
## <a name="examples"></a>Exemplos  
 Os exemplos a seguir mostram o <xref:System.Runtime.Serialization.KnownTypeAttribute> classe em uso.  
  
#### <a name="example-1"></a>Exemplo 1  
 Há três classes com uma relação de herança.  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 O seguinte `CompanyLogo` classe pode ser serializada, mas não pode ser desserializado se o `ShapeOfLogo` membro é definido como um `CircleType` ou um `TriangleType` objeto, pois o mecanismo de desserialização não reconhece qualquer tipo com nomes de contrato de dados " Círculo"ou"Triângulo".  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 A maneira correta de gravar o `CompanyLogo` tipo é mostrado no código a seguir.  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 Sempre que o tipo externo `CompanyLogo2` está sendo desserializado, o mecanismo de desserialização conhece `CircleType` e `TriangleType` e, portanto, é possível localizar tipos de correspondência para os contratos de dados "Círculo" e "Triângulo".  
  
#### <a name="example-2"></a>Exemplo 2  
 No exemplo a seguir, mesmo que ambos `CustomerTypeA` e `CustomerTypeB` tem o `Customer` de contrato de dados, uma instância do `CustomerTypeB` é criado sempre que um `PurchaseOrder` é desserializado, pois apenas `CustomerTypeB` é conhecido para o mecanismo de desserialização.  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a>Exemplo 3:  
 No exemplo a seguir, uma <xref:System.Collections.Hashtable> armazena seu conteúdo internamente como <xref:System.Object>. Para desserializar a uma tabela de hash com êxito, o mecanismo de desserialização deve saber o conjunto de possíveis tipos que podem ocorrer existe. Nesse caso, estamos saber com antecedência que apenas `Book` e `Magazine` são armazenados no `Catalog`, portanto, aqueles são adicionados usando o <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo.  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a>Exemplo 4  
 No exemplo a seguir, um contrato de dados armazena um número e uma operação para executar o número. O `Numbers` membro de dados pode ser um inteiro, uma matriz de inteiros, ou um <xref:System.Collections.Generic.List%601> que contém números inteiros.  
  
> [!CAUTION]
>  Isso só funcionará no lado do cliente se SVCUTIL. EXE é usado para gerar um proxy do WCF. SVCUTIL. EXE recupera metadados do serviço, incluindo quaisquer tipos conhecidos. Sem essas informações um cliente não poderá desserializar os tipos.  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 Este é o código do aplicativo.  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a>Interfaces e herança de tipos conhecidos  
 Quando um tipo conhecido é associado a um tipo específico usando o `KnownTypeAttribute` atributo, o tipo conhecido também é associado a todos os tipos derivados do mesmo tipo. Por exemplo, consulte o código a seguir.  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 O `DoubleDrawing` classe não requer o `KnownTypeAttribute` atributo usar `Square` e `Circle` no `AdditionalShape` campo, porque a classe base (`Drawing`) já tem estes atributos aplicados.  
  
 Tipos conhecidos podem ser associados somente classes e estruturas, interfaces não.  
  
## <a name="known-types-using-open-generic-methods"></a>Tipos conhecidos usando métodos genéricos abertos  
 Pode ser necessário adicionar um tipo genérico como um tipo conhecido. No entanto, um tipo genérico aberto não pode ser passado como um parâmetro para o `KnownTypeAttribute` atributo.  
  
 Esse problema pode ser resolvido por meio de um mecanismo alternativo: escrever um método que retorna uma lista de tipos a serem adicionados à coleção de tipos conhecidos. O nome do método é especificado então como um argumento de cadeia de caracteres para o `KnownTypeAttribute` atributo devido a algumas restrições.  
  
 O método deve existir no tipo ao qual o `KnownTypeAttribute` atributo é aplicado, deve ser estático, não deve aceitar nenhum parâmetro e deve retornar um objeto que pode ser atribuído a <xref:System.Collections.IEnumerable> de <xref:System.Type>.  
  
 Não é possível combinar o `KnownTypeAttribute` atributo com um nome de método e `KnownTypeAttribute` atributos com tipos reais do mesmo tipo. Além disso, você não pode aplicar mais de um `KnownTypeAttribute` com um nome de método para o mesmo tipo.  
  
 Consulte a seguinte classe.  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 O `theDrawing` campo contém instâncias de uma classe genérica `ColorDrawing` e uma classe genérica `BlackAndWhiteDrawing`, que herdam de uma classe genérica `Drawing`. Normalmente, ambos devem ser adicionadas aos tipos conhecidos, mas a seguir não é uma sintaxe válida para os atributos.  
  
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
  
 Assim, um método deve ser criado para esses tipos de retorno. A maneira correta de gravar este tipo, em seguida, é mostrada no código a seguir.  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a>Outras maneiras de adicionar tipos conhecidos  
 Além disso, os tipos conhecidos podem ser adicionados por meio de um arquivo de configuração. Isso é útil quando você não controla o tipo que requer tipos conhecidos para desserialização apropriada, como quando usando terceiros bibliotecas de tipo com [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
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
  
 Na configuração anterior de um tipo de contrato de dados chamado arquivo `MyCompany.Library.Shape` é declarada com `MyCompany.Library.Circle` como um tipo conhecido.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.KnownTypeAttribute>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Object>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>  
 [Tipos conhecidos](../../../../docs/framework/wcf/samples/known-types.md)  
 [Equivalência de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md) (Criando contratos de serviço)
