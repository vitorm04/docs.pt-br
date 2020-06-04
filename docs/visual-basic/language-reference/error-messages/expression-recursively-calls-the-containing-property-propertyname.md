---
title: A expressão chama recursivamente a propriedade que contém '<propertyname>'
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: e3a9f4cf2f4105d2c449813bf0c593860df7d1f0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409498"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a><span data-ttu-id="beb24-102">A expressão chama recursivamente a propriedade que contém '\<propertyname>'</span><span class="sxs-lookup"><span data-stu-id="beb24-102">Expression recursively calls the containing property '\<propertyname>'</span></span>
<span data-ttu-id="beb24-103">Uma instrução no `Set` procedimento de uma definição de propriedade armazena um valor no nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="beb24-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="beb24-104">A abordagem recomendada para manter o valor de uma propriedade é definir uma `Private` variável no contêiner da propriedade e usá-la nos `Get` `Set` procedimentos e.</span><span class="sxs-lookup"><span data-stu-id="beb24-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="beb24-105">O `Set` procedimento deve armazenar o valor de entrada nessa `Private` variável.</span><span class="sxs-lookup"><span data-stu-id="beb24-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="beb24-106">O `Get` procedimento se comporta como um `Function` procedimento, portanto, ele pode atribuir um valor ao nome da propriedade e ao controle de retorno ao encontrar a `End Get` instrução.</span><span class="sxs-lookup"><span data-stu-id="beb24-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="beb24-107">No entanto, a abordagem recomendada é incluir a `Private` variável como o valor em uma [instrução return](../statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="beb24-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="beb24-108">O `Set` procedimento se comporta como um `Sub` procedimento, que não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="beb24-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="beb24-109">Portanto, o nome do procedimento ou da propriedade não tem um significado especial dentro de um `Set` procedimento e você não pode armazenar um valor nele.</span><span class="sxs-lookup"><span data-stu-id="beb24-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="beb24-110">O exemplo a seguir ilustra a abordagem que pode causar esse erro, seguida da abordagem recomendada.</span><span class="sxs-lookup"><span data-stu-id="beb24-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
```vb  
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
  
 <span data-ttu-id="beb24-111">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="beb24-111">By default, this message is a warning.</span></span> <span data-ttu-id="beb24-112">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="beb24-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="beb24-113">**ID do erro:** BC42026</span><span class="sxs-lookup"><span data-stu-id="beb24-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="beb24-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="beb24-114">To correct this error</span></span>  
  
- <span data-ttu-id="beb24-115">Reescreva a definição de propriedade para usar a abordagem recomendada, conforme ilustrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="beb24-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb24-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="beb24-116">See also</span></span>

- [<span data-ttu-id="beb24-117">Procedimentos de propriedade</span><span class="sxs-lookup"><span data-stu-id="beb24-117">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="beb24-118">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="beb24-118">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="beb24-119">Instrução SET</span><span class="sxs-lookup"><span data-stu-id="beb24-119">Set Statement</span></span>](../statements/set-statement.md)
