---
title: "Usando indexadores (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "indexadores [C#], sobre indexadores"
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
caps.latest.revision: 30
caps.handback.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Usando indexadores (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Os indexadores são uma conveniência sintática que permitem que você criar um  [classe](../../../csharp/language-reference/keywords/class.md),  [struct](../../../csharp/language-reference/keywords/struct.md), ou  [interface](../../../csharp/language-reference/keywords/interface.md) que os aplicativos cliente podem acessar apenas como uma matriz.  Indexadores são mais frequentemente implementados em tipos cujo objetivo principal é encapsular uma coleção interna ou array.  Por exemplo, suponha que você tenha uma classe chamada TempRecord que representa a temperatura em Farenheit gravada 10 vezes diferentes durante um período de 24 horas.  A classe contém uma matriz chamada "temps" de tipo flutuante para representar as temperaturas e um <xref:System.DateTime> que representa a data em que as temperaturas foram registradas.  Implementando um indexador nesta classe, os clientes podem acessar as temperaturas em uma instância de TempRecord como `float temp = tr[4]` em vez de como `float temp = tr.temps[4]`.  A notação do indexador não apenas simplifica a sintaxe para aplicativos do cliente. Ele também torna a classe e sua finalidade mais intuitiva para outros desenvolvedores entender.  
  
 Para declarar um indexador em uma classe ou struct, use o  [Este](../../../csharp/language-reference/keywords/this.md) palavra\-chave, como no exemplo:  
  
```  
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
  
```  
  
## Comentários  
 O tipo de um indexador e o tipo de seus parâmetros devem ser pelo menos tão acessíveis quanto o próprio indexador.  Para obter mais informações sobre os níveis de acessibilidade, consulte  [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Para obter mais informações sobre como usar indexadores com uma interface, consulte  [Interface indexadores](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).  
  
 A assinatura de um indexador consiste do número e tipos de seus parâmetros formais.  Isso não inclui o tipo de indexador ou os nomes dos parâmetros formais.  Se você declarar mais do que um indexador na mesma classe, eles devem ter diferentes assinaturas.  
  
 Um valor do indexador não é classificado como uma variável; Portanto, você não pode passar um valor de indexador como um  [ref](../../../csharp/language-reference/keywords/ref.md) ou  [check\-out](../../../csharp/language-reference/keywords/out.md) parâmetro.  
  
 Para fornecer um nome que outras linguagens podem usar o indexador, use um `name` atributo na declaração.  Por exemplo:  
  
```  
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this [int index]   // Indexer declaration  
{  
}  
```  
  
 Este indexador terá o nome `TheItem`.  Não está fornecendo o atributo name tornaria `Item` o nome padrão.  
  
## Exemplo 1  
  
### Descrição  
 O exemplo a seguir mostra como declarar um campo particular do array, `temps`e um indexador.  O indexador permite acesso direto à ocorrência de `tempRecord[i]`.  Uma alternativa ao uso do indexador é declarar a matriz como uma  [pública](../../../csharp/language-reference/keywords/public.md) membro e acessar seus membros, `tempRecord.temps[i]`, diretamente.  
  
 Observe que, quando o acesso de um indexador é avaliado, por exemplo, em um `Console.Write` instrução, o  [obter](../../../csharp/language-reference/keywords/get.md) acessador é invocado.  Portanto, se nenhum `get` acessador existe, ocorrerá um erro em tempo de compilação.  
  
### Código  
 [!code-cs[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]  
  
## Usando outros valores de indexação  
 C\# não limita o tipo do indexador a um inteiro.  Por exemplo, pode ser útil usar um string com um indexador.  Tal indexador pode ser implementado pesquisando a string na coleção, e retornando o valor apropriado.  Como os accessores podem ser sobrecarregados, as versões string e inteiros pode coexistirem.  
  
## Exemplo 2  
  
### Descrição  
 Neste exemplo, uma classe é declarada que armazena os dias da semana.  A `get` o acessador é declarado que leva uma seqüência de caracteres, o nome de um dia e retorna o inteiro correspondente.  Por exemplo, Domingo irá retornar 0, Segunda irá retornar 1, e assim sucessivamente.  
  
### Código  
 [!code-cs[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## Programação robusta  
 Há duas formas principais em que a segurança e a confiabilidade dos indexadores podem ser melhoradas:  
  
-   Certfique\-se que algum tipo de estratégia de tratamento de erro seja incorporado para tratar a chance do código cliente passar um valor de índice inválido.  No primeiro exemplo neste tópico, a classe TempRecord fornece uma propriedade Length que permite o código do cliente verificar a entrada antes de passá\-la para o indexador.  Você pode também colocar o código de tratamento de erro dentro do próprio indexador.  Certifique\-se que qualquer exceção que você lançar dentro de um accessor de indexador seja documentada para usuários.  
  
-   Definir a acessibilidade da `get` e  [set](../../../csharp/language-reference/keywords/set.md) acessadores para serem os mais restritivos é razoável.  Isso é importante para o `set` acessador em particular.  Para obter mais informações, consulte [Restringindo a acessibilidade aos acessadores](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Indexadores](../../../csharp/programming-guide/indexers/index.md)   
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)