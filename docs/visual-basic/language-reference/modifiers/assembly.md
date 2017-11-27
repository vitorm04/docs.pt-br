---
title: Assembly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef4434f0bc520abfc621567fc68e0b8bcfd6e381
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-visual-basic"></a>Assembly (Visual Basic)
Especifica que um atributo no início de um arquivo de origem se aplica ao assembly inteiro.  
  
## <a name="remarks"></a>Comentários  
 Muitos atributos referem-se a um elemento de programação individual, como uma classe ou propriedade. Aplicar um atributo, anexando o bloco de atributo, entre colchetes angulares (`< >`), diretamente à instrução de declaração.  
  
 Se um atributo pertence não apenas ao seguinte elemento mas ao conjunto inteiro, você coloca o bloco de atributo no início do arquivo de origem e identifica o atributo com o `Assembly` palavra-chave. Se ele se aplica ao módulo assembly atual, você usar o [módulo](../../../visual-basic/language-reference/modifiers/module-keyword.md) palavra-chave.  
  
 Você também pode aplicar um atributo a um assembly no arquivo AssemblyInfo vb, caso em que você não precisa usar um bloco de atributo em seu arquivo de código-fonte principal.  
  
## <a name="see-also"></a>Consulte também  
 [Módulo \<palavra-chave >](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)

