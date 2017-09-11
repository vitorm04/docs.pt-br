---
title: "Como: determinar que tipo uma variável de objeto se refere (Visual Basic) | Documentos do Microsoft"
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
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables, determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
caps.latest.revision: 13
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: cb090540d7c5792753ff62c529603947ec5a8e96
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="b446e-102">Como determinar a que tipo uma variável de objeto se refere (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b446e-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>
<span data-ttu-id="b446e-103">Uma variável de objeto contém um ponteiro para dados armazenados em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="b446e-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="b446e-104">O tipo de dados que pode alterar durante o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b446e-104">The type of that data can change during run time.</span></span> <span data-ttu-id="b446e-105">A qualquer momento, você pode usar o <xref:System.Type.GetTypeCode%2A>método para determinar o tipo de tempo de execução atual, ou o [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md) para descobrir se o atual tipo de tempo de execução é compatível com um tipo especificado.</xref:System.Type.GetTypeCode%2A></span><span class="sxs-lookup"><span data-stu-id="b446e-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="b446e-106">Para determinar que a exata tipo a uma variável de objeto atualmente refere-se a</span><span class="sxs-lookup"><span data-stu-id="b446e-106">To determine the exact type an object variable currently refers to</span></span>  
  
1.  <span data-ttu-id="b446e-107">Na variável de objeto, chame o <xref:System.Object.GetType%2A>método para recuperar um <xref:System.Type?displayProperty=fullName>objeto.</xref:System.Type?displayProperty=fullName> </xref:System.Object.GetType%2A></span><span class="sxs-lookup"><span data-stu-id="b446e-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=fullName> object.</span></span>  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  <span data-ttu-id="b446e-108">Sobre o <xref:System.Type?displayProperty=fullName>da classe, chame o método compartilhado <xref:System.Type.GetTypeCode%2A>para recuperar o <xref:System.TypeCode>valor de enumeração para o tipo de objeto.</xref:System.TypeCode> </xref:System.Type.GetTypeCode%2A> </xref:System.Type?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b446e-108">On the <xref:System.Type?displayProperty=fullName> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     <span data-ttu-id="b446e-109">Você pode testar a <xref:System.TypeCode>contra qualquer enumeração membros são de interesse, como valor da enumeração `Double`.</xref:System.TypeCode></span><span class="sxs-lookup"><span data-stu-id="b446e-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="b446e-110">Para determinar se um objeto de tipo de variável é compatível com um tipo especificado</span><span class="sxs-lookup"><span data-stu-id="b446e-110">To determine whether an object variable's type is compatible with a specified type</span></span>  
  
-   <span data-ttu-id="b446e-111">Use o `TypeOf` operador em combinação com o [operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) para testar o objeto com um `TypeOf`... `Is` expressão.</span><span class="sxs-lookup"><span data-stu-id="b446e-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     <span data-ttu-id="b446e-112">The `TypeOf`... `Is` retorna `True` se o objeto do tempo de execução tipo é compatível com o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="b446e-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>  
  
     <span data-ttu-id="b446e-113">O critério para compatibilidade depende se o tipo especificado é uma classe, estrutura ou interface.</span><span class="sxs-lookup"><span data-stu-id="b446e-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="b446e-114">Em geral, os tipos são compatíveis se o objeto é do mesmo tipo como, herda de ou implementa o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="b446e-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="b446e-115">Para obter mais informações, consulte [operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b446e-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b446e-116">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b446e-116">Compiling the Code</span></span>  
 <span data-ttu-id="b446e-117">Observe que o tipo especificado não pode ser uma variável ou expressão.</span><span class="sxs-lookup"><span data-stu-id="b446e-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="b446e-118">Ele deve ser o nome de um tipo definido, como uma classe, estrutura ou interface.</span><span class="sxs-lookup"><span data-stu-id="b446e-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="b446e-119">Isso inclui tipos intrínsecos como `Integer` e `String`.</span><span class="sxs-lookup"><span data-stu-id="b446e-119">This includes intrinsic types such as `Integer` and `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b446e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b446e-120">See Also</span></span>  
 <span data-ttu-id="b446e-121"><xref:System.Object.GetType%2A></xref:System.Object.GetType%2A></span><span class="sxs-lookup"><span data-stu-id="b446e-121"><xref:System.Object.GetType%2A></span></span>   
 <span data-ttu-id="b446e-122"><xref:System.Type?displayProperty=fullName></xref:System.Type?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b446e-122"><xref:System.Type?displayProperty=fullName></span></span>   
 <span data-ttu-id="b446e-123"><xref:System.Type.GetTypeCode%2A></xref:System.Type.GetTypeCode%2A></span><span class="sxs-lookup"><span data-stu-id="b446e-123"><xref:System.Type.GetTypeCode%2A></span></span>   
 <span data-ttu-id="b446e-124"><xref:System.TypeCode></xref:System.TypeCode></span><span class="sxs-lookup"><span data-stu-id="b446e-124"><xref:System.TypeCode></span></span>   
<span data-ttu-id="b446e-125"> [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="b446e-125"> [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="b446e-126"> [Valores de variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span><span class="sxs-lookup"><span data-stu-id="b446e-126"> [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span></span>  
<span data-ttu-id="b446e-127"> [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="b446e-127"> [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)</span></span>
