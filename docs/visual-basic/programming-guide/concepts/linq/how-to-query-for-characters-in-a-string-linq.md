---
title: 'Como: consultar caracteres em uma cadeia de caracteres (Visual Basic) (LINQ) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dabd63e52707f3078c6cdc41db8c4f0e7dfbf70e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a>Como: consultar caracteres em uma cadeia de caracteres (LINQ) (Visual Basic)
Porque o <xref:System.String>classe implementa a <xref:System.Collections.Generic.IEnumerable%601>interface, qualquer cadeia de caracteres pode ser consultada como uma sequência de caracteres.</xref:System.Collections.Generic.IEnumerable%601> </xref:System.String> No entanto, isso não é um uso comum do LINQ. Para operações de correspondência de padrões complexos, use a <xref:System.Text.RegularExpressions.Regex>classe.</xref:System.Text.RegularExpressions.Regex>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir consulta uma cadeia de caracteres para determinar o número de dígitos numéricos que ele contém. Observe que a consulta é "reutilizada" depois que ele é executado na primeira vez. Isso é possível porque a consulta em si não armazena os resultados reais.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## <a name="compiling-the-code"></a>Compilando o código  
 Criar um projeto que tem como alvo o .NET Framework versão 3.5 ou superior com uma referência a System.Core.dll e uma `Imports` declaração para o namespace System. Linq.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ e cadeias de caracteres (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)   
 [Como: combinar consultas LINQ com expressões regulares (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
