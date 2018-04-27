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
ms.openlocfilehash: d7693e712884a500495e4573900e7d9a049c2879
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="nothing-and-strings-in-visual-basic"></a>Nada e cadeias de caracteres no Visual Basic
O tempo de execução do Visual Basic e o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] avaliar `Nothing` diferente quando se trata de cadeias de caracteres.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Tempo de execução do Visual Basic e o .NET Framework  
 Considere o exemplo a seguir:  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 O tempo de execução do Visual Basic geralmente avalia `Nothing` como uma cadeia de caracteres vazia (""). O [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] não e gera uma exceção sempre que é feita uma tentativa de executar uma operação de cadeia de caracteres em `Nothing`.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução às cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
