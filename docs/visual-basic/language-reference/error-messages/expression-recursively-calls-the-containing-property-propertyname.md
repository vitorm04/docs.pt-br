---
title: "A expressão chama recursivamente a propriedade recipiente &quot;&lt;propertyname&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42026
- BC42026
dev_langs:
- VB
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
caps.latest.revision: 10
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
ms.openlocfilehash: c7168ab2a2ec5eb0c0d423120b67c10b117c14b2
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a><span data-ttu-id="3bcab-102">A expressão chama recursivamente a propriedade recipiente '&lt;propertyname&gt;'</span><span class="sxs-lookup"><span data-stu-id="3bcab-102">Expression recursively calls the containing property &#39;&lt;propertyname&gt;&#39;</span></span>
<span data-ttu-id="3bcab-103">Uma instrução no `Set` procedimento de uma definição de propriedade armazena um valor no nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="3bcab-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="3bcab-104">A abordagem recomendada para armazenar o valor de uma propriedade é definir uma `Private` variável no recipiente da propriedade e usá-lo em ambos os `Get` e `Set` procedimentos.</span><span class="sxs-lookup"><span data-stu-id="3bcab-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="3bcab-105">O `Set` procedimento deve então armazenar o valor de entrada nesta `Private` variável.</span><span class="sxs-lookup"><span data-stu-id="3bcab-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="3bcab-106">O `Get` procedimento se comporta como um `Function` procedimento, para que possa atribuir um valor ao nome da propriedade e retornar controle encontrando o `End Get` instrução.</span><span class="sxs-lookup"><span data-stu-id="3bcab-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="3bcab-107">A abordagem recomendada, entretanto, é incluir a `Private` variável como o valor em uma [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3bcab-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="3bcab-108">O `Set` procedimento se comporta como uma `Sub` procedimento, que não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="3bcab-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="3bcab-109">Portanto, o nome do procedimento ou propriedade não tem significado especial em uma `Set` procedimento e você não pode armazenar um valor nele.</span><span class="sxs-lookup"><span data-stu-id="3bcab-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="3bcab-110">O exemplo a seguir ilustra a abordagem que pode causar esse erro, seguido pela abordagem recomendada.</span><span class="sxs-lookup"><span data-stu-id="3bcab-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
```  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 <span data-ttu-id="3bcab-111">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="3bcab-111">By default, this message is a warning.</span></span> <span data-ttu-id="3bcab-112">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3bcab-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="3bcab-113">**ID do erro:** BC42026</span><span class="sxs-lookup"><span data-stu-id="3bcab-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3bcab-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="3bcab-114">To correct this error</span></span>  
  
-   <span data-ttu-id="3bcab-115">Reescreva a definição de propriedade para usar a abordagem recomendada, conforme ilustrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="3bcab-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bcab-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3bcab-116">See Also</span></span>  
 <span data-ttu-id="3bcab-117">[Procedimentos de propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="3bcab-117">[Property Procedures](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) </span></span>  
<span data-ttu-id="3bcab-118"> [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="3bcab-118"> [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="3bcab-119"> [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)</span><span class="sxs-lookup"><span data-stu-id="3bcab-119"> [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md)</span></span>
