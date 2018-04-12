---
title: Nada e cadeias de caracteres no Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ce9f81f23f50e38f6b1ad5e638e8c6ac026e992
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="nothing-and-strings-in-visual-basic"></a>Nada e cadeias de caracteres no Visual Basic
O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tempo de execução e o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] avaliar `Nothing` diferente quando se trata de cadeias de caracteres.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Tempo de execução do Visual Basic e o .NET Framework  
 Considere o exemplo a seguir:  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tempo de execução geralmente avalia `Nothing` como uma cadeia de caracteres vazia (""). O [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] não e gera uma exceção sempre que é feita uma tentativa de executar uma operação de cadeia de caracteres em `Nothing`.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução às cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
