---
title: "Foi criada uma referência ao assembly de interoperabilidade inserido &quot;&lt;assembly1&gt;&quot;devido a uma referência indireta ao assembly do assembly&quot;&lt;assembly2&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6d7f7936eb09b3dcf1355125adb40141068a927c
ms.lasthandoff: 03/13/2017

---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a>Foi criada uma referência ao assembly de interoperabilidade inserido '&lt;assembly1&gt;'devido a uma referência indireta ao assembly do assembly'&lt;assembly2&gt;'
Foi criada uma referência ao assembly de interoperabilidade inserido '\<assembly1 >' devido a uma referência indireta ao assembly do assembly '\<assembly2 >'. Considere alterar a propriedade 'Inserir tipos Interop' em um assembly.  
  
 Você adicionou uma referência a um assembly (assembly1) que tem o `Embed Interop Types` definida como `True`. Isso instrui o compilador a inserir informações de tipo de interoperabilidade do assembly. No entanto, o compilador não pode inserir informações de tipo de interoperabilidade do assembly porque outro assembly que você referenciou (assembly2) também faz referência a esse assembly (assembly1) e tem o `Embed Interop Types` definida como `False`.  
  
> [!NOTE]
>  Definindo o `Embed Interop Types` propriedade em uma referência de assembly para `True` é equivalente à referência do assembly usando o `/link` opção para o compilador de linha de comando.  
  
 **ID do erro:** BC40059  
  
### <a name="to-address-this-warning"></a>Para resolver este aviso  
  
-   Para inserir informações de tipo de interoperabilidade para os dois assemblies, definir o `Embed Interop Types` propriedade em todas as referências a assembly1 para `True`.  
  
-   Para remover o aviso, você pode definir o `Embed Interop Types` propriedade assembly1 para `False`. Nesse caso, as informações de tipo de interoperabilidade são fornecidas por um assembly de interoperabilidade primária (PIA).  
  
## <a name="see-also"></a>Consulte também  
 [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)   
 [Programação com Assemblies de interoperabilidade primários](http://msdn.microsoft.com/en-us/306fa1d6-0703-4004-9e93-d0a57f1be81e)
