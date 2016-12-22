---
title: "Foi criada uma refer&#234;ncia para o assembly de interoperabilidade inserido &#39;&lt;assembly1&gt;&#39; devido a uma refer&#234;ncia indireta a esse assembly a partir do assembly &#39;&lt;assembly2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40059"
  - "bc40059"
helpviewer_keywords: 
  - "BC40059"
  - "VBC40059"
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Foi criada uma refer&#234;ncia para o assembly de interoperabilidade inserido &#39;&lt;assembly1&gt;&#39; devido a uma refer&#234;ncia indireta a esse assembly a partir do assembly &#39;&lt;assembly2&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma referência foi criada para o assembly de interoperabilidade incorporado '\<assembly1\> ' por causa de uma referência indireta ao assembly do assembly '\<assembly2\> '.Considere alterar a propriedade 'Incorporar tipos de interoperabilidade' em um assembly.  
  
 Você adicionou uma referência a um assembly \(assembly1\) que tem o `Embed Interop Types` propriedade definida como `True`.  Isso instrui o compilador para incorporar informações de tipo de interoperabilidade a partir desse assembly.  No entanto, o compilador não pode incorporar informações de tipo de interoperabilidade desse assembly porque outro assembly que você referenciou \(assembly2\) também faz referência a esse assembly \(assembly1\) e tem o `Embed Interop Types` propriedade definida como `False`.  
  
> [!NOTE]
>  Definindo a `Embed Interop Types` propriedade em uma referência de assembly para `True` é equivalente a referência ao assembly usando o `/link` opção para o compilador de linha de comando.  
  
 **Identificação do erro:**  BC40059  
  
### Para resolver esse aviso  
  
-   Para incorporar informações de tipo de interoperabilidade para os dois assemblies, defina a `Embed Interop Types` propriedade em todas as referências a assembly1 para `True`.  
  
-   Para remover o aviso, você pode definir a `Embed Interop Types` propriedade de assembly1 para `False`.  Nesse caso, as informações de tipo de interoperabilidade são fornecidas por um assembly de interoperabilidade primária \(PIA\).  
  
## Consulte também  
 [\/link](../../../visual-basic/reference/command-line-compiler/link.md)   
 [Programming with Primary Interop Assemblies](http://msdn.microsoft.com/pt-br/306fa1d6-0703-4004-9e93-d0a57f1be81e)