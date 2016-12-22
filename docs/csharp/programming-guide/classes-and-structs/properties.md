---
title: "Propriedades (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.properties"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Linguagem C#, propriedades"
  - "propriedades [C#]"
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
caps.latest.revision: 38
caps.handback.revision: 38
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Propriedades (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma propriedade é um membro que oferece um mecanismo flexível para leitura, gravação ou calcular o valor de um campo particular.  Propriedades podem ser usadas como se eles são membros de dados públicos, mas são métodos realmente especiais chamados *acessadores*.  Isso permite que os dados sejam acessados facilmente e ainda ajuda a promover a segurança e a flexibilidade dos métodos.  
  
 Neste exemplo, a `TimePeriod` classe armazena um período de tempo.  A classe armazena internamente o tempo em segundos, mas uma propriedade chamada `Hours` permite que um cliente especificar um tempo em horas.  Os acessadores para o `Hours` propriedade executar a conversão entre horas e segundos.  
  
## Exemplo  
 [!code-cs[csProgGuideProperties#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/properties_1.cs)]  
  
## Definições de corpo da expressão  
 É comum ter propriedades que simplesmente retornam imediatamente com o resultado de uma expressão.  Existe um atalho de sintaxe para definir essas propriedades usando `=>`:  
  
```c#  
public string Name => First + " " + Last;   
```  
  
 A propriedade deve ser somente leitura e não usar o `get` palavra\-chave do acessador.  
  
## Visão geral das propriedades  
  
-   As propriedades permitem uma classe para expor uma maneira pública de obter e definir valores, ocultando o código de implementação ou verificação.  
  
-   Um [obter](../../../csharp/language-reference/keywords/get.md) acessador de propriedade é usado para retornar o valor da propriedade e um [definir](../../../csharp/language-reference/keywords/set.md) acessador é usado para atribuir um novo valor.  Esses acessadores podem ter diferentes níveis de acesso.  Para obter mais informações, consulte [Restringindo a acessibilidade aos acessadores](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
-   O [valor](../../../csharp/language-reference/keywords/value.md) palavra\-chave é usada para definir o valor que está sendo atribuído pelo `set` acessador.  
  
-   Propriedades que não implementam um `set` acessador são somente leitura.  
  
-   Para propriedades simples que não exigem nenhum código personalizado do acessador, considere a opção de usar as propriedades implementadas automaticamente.  Para obter mais informações, consulte [Propriedades autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## Seções relacionadas  
  
-   [Usando propriedades](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [Propriedades de interface](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [Comparação entre propriedades e indexadores](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [Restringindo a acessibilidade aos acessadores](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
-   [Propriedades autoimplementadas](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Usando propriedades](../../../csharp/programming-guide/classes-and-structs/using-properties.md)   
 [Indexadores](../../../csharp/programming-guide/indexers/index.md)