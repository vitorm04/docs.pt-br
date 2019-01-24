---
title: Nada e cadeias de caracteres no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 65a69861c2a74a3191a45eb782a97f289b0c0726
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574164"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Nada e cadeias de caracteres no Visual Basic
O tempo de execução do Visual Basic e o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] avaliar `Nothing` diferente quando se trata de cadeias de caracteres.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Tempo de execução do Visual Basic e o .NET Framework  
 Considere o exemplo a seguir:  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 O tempo de execução do Visual Basic geralmente avalia `Nothing` como uma cadeia de caracteres vazia (""). O [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] não e gera uma exceção sempre que for feita uma tentativa de executar uma operação de cadeia de caracteres em `Nothing`.  
  
## <a name="see-also"></a>Consulte também
- [Introdução às cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
