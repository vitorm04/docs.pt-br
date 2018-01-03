---
title: "Foi criada uma referência ao assembly de interoperabilidade inserido &#39; &lt;assembly1&gt;&#39; devido a uma referência indireta ao assembly do assembly &#39;&lt; assembly2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aaaa7460ade00ad4232807ce11ee125e270742bf
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a>Foi criada uma referência ao assembly de interoperabilidade inserido &#39; &lt;assembly1&gt;&#39; devido a uma referência indireta ao assembly do assembly &#39;&lt; assembly2&gt;&#39;
Foi criada uma referência para o assembly de interoperabilidade inserido '\<assembly1>' devido a uma referência indireta a esse assembly do assembly '\<assembly2>'. Considere alterar a propriedade 'Inserir Tipos de Interoperabilidade' em um dos assemblies.  
  
 Você adicionou uma referência a um assembly (assembly1) que tem a propriedade `Embed Interop Types` definida como `True`. Isso instrui o compilador a inserir informações de tipo de interoperabilidade desse assembly. No entanto, o compilador não pode inserir informações de tipo de interoperabilidade desse assembly, porque outro assembly que você referenciou (assembly2) também faz referência a esse assembly (assembly1) e tem a propriedade `Embed Interop Types` definida como `False`.  
  
> [!NOTE]
>  Configurar a propriedade `Embed Interop Types` em uma referência de assembly como `True` é equivalente à referenciar o assembly usando a opção `/link` para o compilador de linha de comando.  
  
 **ID do erro:** BC40059  
  
### <a name="to-address-this-warning"></a>Para resolver este aviso  
  
-   Para inserir informações de tipo de interoperabilidade para os dois assemblies, defina a propriedade `Embed Interop Types` em todas as referências ao assembly1 como `True`.  
  
-   Para remover o aviso, você pode definir a propriedade `Embed Interop Types` do assembly1 como `False`. Nesse caso, as informações de tipo de interoperabilidade são fornecidas por um assembly de interoperabilidade primária (PIA).  
  
## <a name="see-also"></a>Consulte também  
 [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)  
 [Interoperação com código não gerenciado](../../../framework/interop/index.md)
