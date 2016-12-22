---
title: "Como: declarar e usar propriedades de grava&#231;&#227;o de leitura (guia de programa&#231;&#227;o c#) | Microsoft Docs"
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
  - "acessador Get [c#], declarando propriedades"
  - "acessador set [C#]"
  - "Propriedades [c#], declarando"
  - "propriedades de leitura/gravação [C#]"
  - "acessadores [c#], declarando propriedades com"
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: declarar e usar propriedades de grava&#231;&#227;o de leitura (guia de programa&#231;&#227;o c#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Propriedades fornecem a conveniência de membros de dados públicos sem os riscos que vêm com acesso desprotegido, não\-controlado e não\-verificado para dados de um objeto.  Isso é realizado através de  *acessadores*: métodos especiais que atribuir e recuperam valores do membro de dados subjacente.  O  [set](../../../csharp/language-reference/keywords/set.md) acessador permite que os membros de dados seja atribuído e o  [obter](../../../csharp/language-reference/keywords/get.md) acessador recupera os valores de membro de dados.  
  
 Esse exemplo mostra um `Person` classe tem duas propriedades: `Name` \(string\) e `Age` \(int\).  Ambas as propriedades fornecem `get` e `set` propriedades de leitura\/gravação acessadores, portanto são consideradas.  
  
## Exemplo  
 [!code-cs[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## Programação robusta  
 No exemplo anterior, o `Name` e `Age` propriedades são  [pública](../../../csharp/language-reference/keywords/public.md) e incluir ambos um `get` e um `set` acessador.  Isso permite que qualquer objeto ler e gravar essas propriedades.  No entanto, às vezes é desejável, excluir um dos acessadores.  Omitindo o `set` acessador, por exemplo, faz a propriedade somente leitura:  
  
 [!code-cs[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 Como alternativa, você pode expor um assessor publicamente, mas tornar os outros particular ou protegido.  Para obter mais informações, consulte  [Acessibilidade do acessador assimétrica](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
 Depois que as propriedades são declaradas, eles podem ser usados como se fossem campos da classe.  Isso permite uma sintaxe muito natural quando tanto Obtendo e definindo o valor de uma propriedade, como nas instruções a seguir:  
  
 [!code-cs[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 Observe que em uma propriedade `set` método um especial `value` variável está disponível.  Essa variável contém o valor que o usuário especificou como, por exemplo:  
  
 [!code-cs[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 Observe a sintaxe limpa para incrementar o `Age` propriedade em um `Person` objeto:  
  
 [!code-cs[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 Se separado `set` e `get` foram usados métodos para modelar a propriedades, o código equivalente teria esta aparência:  
  
```  
person.SetAge(person.GetAge() + 1);   
```  
  
 O `ToString` método é substituído neste exemplo:  
  
 [!code-cs[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 Observe que `ToString` não é explicitamente usado no programa.  Ele é invocado por padrão, o `WriteLine` chamadas.  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)