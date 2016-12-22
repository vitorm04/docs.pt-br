---
title: "Exemplo de classe COM (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "COM, expondo objetos do Visual C# a"
  - "exemplos [C#], classes COM"
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Exemplo de classe COM (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este é um exemplo de uma classe que você poderia expor como um objeto COM.  Depois que esse código é colocado em um arquivo. cs e adicionado ao seu projeto, defina a  **Register for COM Interop** propriedade para  **True**.  Para obter mais informações, consulte [NIB: How to: Register a Component for COM Interop](http://msdn.microsoft.com/pt-br/4de7d474-56e8-4027-994d-d47ca4725c5e).  
  
 Expor objetos Visual C\# COM requer a declaração de uma interface de classe, uma interface de eventos, se necessário e a própria classe.  Membros de classe devem seguir estas regras para estar visível para COM:  
  
-   A classe deve ser pública.  
  
-   Propriedades, métodos e eventos devem ser públicos.  
  
-   Propriedades e métodos devem ser declarados na interface de classe.  
  
-   Eventos devem ser declarados o interface.  
  
 Outros membros públicos na classe que não sejam declarados nessas interfaces não ficará visíveis para COM, mas eles estarão visíveis aos outros.Objetos do NET Framework.  
  
 Para expor propriedades e métodos para COM, você deve declará\-los na interface de classe e marcá\-las com um `DispId` de atributo e implementá\-los na classe.  A ordem em que os membros são declarados na interface é a ordem usada para o COM vtable.  
  
 Para expor eventos de sua classe, você deve declará\-los na interface de eventos e marcá\-las com um `DispId` atributo.  A classe não deve implementar esta interface.  
  
 A classe implementa a interface de classe; ele pode implementar mais de uma interface, mas a primeira implementação será a interface de classe padrão.  Implemente os métodos e propriedades expostas a COM aqui.  Eles devem ser marcados como públicos e devem coincidir com as declarações na interface de classe.  Além disso, declare os eventos gerados pela classe aqui.  Eles devem ser marcados como públicos e devem coincidir com as declarações na interface de eventos.  
  
## Exemplo  
 [!code-cs[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Interoperabilidade](../../../csharp/programming-guide/interop/interoperability.md)   
 [Página de Compilação, Designer de Projeto \(C\#\)](/visual-studio/ide/reference/build-page-project-designer-csharp)