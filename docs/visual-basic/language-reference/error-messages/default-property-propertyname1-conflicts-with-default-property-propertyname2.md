---
title: A propriedade padrão '<propertyname1>' está em conflito com a propriedade padrão '<propertyname2>' em '<classname>' e por isso deve ser declarada como 'Shadows'
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 37f98ce8120d5861552819690f9d5f22c9959a0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409719"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="24de1-102">A propriedade padrão '\<propertyname1>' está em conflito com a propriedade padrão '\<propertyname2>' em '\<classname>' e por isso deve ser declarada como 'Shadows'</span><span class="sxs-lookup"><span data-stu-id="24de1-102">Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>
<span data-ttu-id="24de1-103">Uma propriedade é declarada com o mesmo nome de uma propriedade definida na classe base.</span><span class="sxs-lookup"><span data-stu-id="24de1-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="24de1-104">Nessa situação, a propriedade nessa classe deve sombrear a propriedade da classe base.</span><span class="sxs-lookup"><span data-stu-id="24de1-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="24de1-105">Esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="24de1-105">This message is a warning.</span></span> <span data-ttu-id="24de1-106">`Shadows`é assumido por padrão.</span><span class="sxs-lookup"><span data-stu-id="24de1-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="24de1-107">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="24de1-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="24de1-108">**ID do erro:** BC40007</span><span class="sxs-lookup"><span data-stu-id="24de1-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="24de1-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="24de1-109">To correct this error</span></span>  
  
- <span data-ttu-id="24de1-110">Adicione a `Shadows` palavra-chave à declaração ou altere o nome da propriedade que está sendo declarada.</span><span class="sxs-lookup"><span data-stu-id="24de1-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24de1-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="24de1-111">See also</span></span>

- [<span data-ttu-id="24de1-112">Sombras</span><span class="sxs-lookup"><span data-stu-id="24de1-112">Shadows</span></span>](../modifiers/shadows.md)
- [<span data-ttu-id="24de1-113">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24de1-113">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
