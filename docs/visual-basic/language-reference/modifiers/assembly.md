---
title: Assembly (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
dev_langs:
- VB
helpviewer_keywords:
- Assembly modifier
- Assembly keyword
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: b496b96360ff891554ab71ba2b3227b2dabbc416
ms.lasthandoff: 03/13/2017

---
# <a name="assembly-visual-basic"></a>Assembly (Visual Basic)
Especifica que um atributo no início de um arquivo de origem se aplica ao conjunto inteiro.  
  
## <a name="remarks"></a>Comentários  
 Muitos atributos referem-se a um elemento de programação individual, como uma classe ou propriedade. Você aplicar tal um atributo, anexando o bloco de atributo, entre colchetes angulares (`< >`), diretamente à instrução de declaração.  
  
 Se um atributo pertence não apenas ao seguinte elemento mas ao conjunto inteiro, você coloca o bloco de atributo no início do arquivo de origem e identifica o atributo com o `Assembly` palavra-chave. Se ele se aplica ao módulo do assembly atual, você usar o [módulo](../../../visual-basic/language-reference/modifiers/module-keyword.md) palavra-chave.  
  
 Você também pode aplicar um atributo a um assembly no arquivo AssemblyInfo vb, caso em que você não precisa usar um bloco de atributo em seu arquivo de código-fonte principal.  
  
## <a name="see-also"></a>Consulte também  
 [Módulo \<palavra-chave >](../../../visual-basic/language-reference/modifiers/module-keyword.md)   
 [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)


