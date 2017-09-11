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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dabd63e52707f3078c6cdc41db8c4f0e7dfbf70e
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="f52fc-102">Como: consultar caracteres em uma cadeia de caracteres (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f52fc-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="f52fc-103">Porque o <xref:System.String>classe implementa a <xref:System.Collections.Generic.IEnumerable%601>interface, qualquer cadeia de caracteres pode ser consultada como uma sequência de caracteres.</xref:System.Collections.Generic.IEnumerable%601> </xref:System.String></span><span class="sxs-lookup"><span data-stu-id="f52fc-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="f52fc-104">No entanto, isso não é um uso comum do LINQ.</span><span class="sxs-lookup"><span data-stu-id="f52fc-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="f52fc-105">Para operações de correspondência de padrões complexos, use a <xref:System.Text.RegularExpressions.Regex>classe.</xref:System.Text.RegularExpressions.Regex></span><span class="sxs-lookup"><span data-stu-id="f52fc-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f52fc-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f52fc-106">Example</span></span>  
 <span data-ttu-id="f52fc-107">O exemplo a seguir consulta uma cadeia de caracteres para determinar o número de dígitos numéricos que ele contém.</span><span class="sxs-lookup"><span data-stu-id="f52fc-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="f52fc-108">Observe que a consulta é "reutilizada" depois que ele é executado na primeira vez.</span><span class="sxs-lookup"><span data-stu-id="f52fc-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="f52fc-109">Isso é possível porque a consulta em si não armazena os resultados reais.</span><span class="sxs-lookup"><span data-stu-id="f52fc-109">This is possible because the query itself does not store any actual results.</span></span>  
  
<span data-ttu-id="f52fc-110"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="f52fc-110"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
## <a name="compiling-the-code"></a><span data-ttu-id="f52fc-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f52fc-111">Compiling the Code</span></span>  
 <span data-ttu-id="f52fc-112">Criar um projeto que tem como alvo o .NET Framework versão 3.5 ou superior com uma referência a System.Core.dll e uma `Imports` declaração para o namespace System. Linq.</span><span class="sxs-lookup"><span data-stu-id="f52fc-112">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f52fc-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f52fc-113">See Also</span></span>  
 <span data-ttu-id="f52fc-114">[LINQ e cadeias de caracteres (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span><span class="sxs-lookup"><span data-stu-id="f52fc-114">[LINQ and Strings (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span></span>  
<span data-ttu-id="f52fc-115"> [Como: combinar consultas LINQ com expressões regulares (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="f52fc-115"> [How to: Combine LINQ Queries with Regular Expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)</span></span>
