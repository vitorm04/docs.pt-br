---
title: 'How to: Read Application Settings'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 04726381f8d285ae61045d1624b3b41b7f47e491
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329563"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="0445f-102">Como ler configurações do aplicativo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0445f-102">How to: Read Application Settings in Visual Basic</span></span>

<span data-ttu-id="0445f-103">Você pode ler uma configuração de usuário, acessando a propriedade da configuração no objeto `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="0445f-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="0445f-104">O objeto `My.Settings` expõe cada configuração como uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="0445f-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="0445f-105">O nome da propriedade é o mesmo que o nome da configuração e o tipo de propriedade é o mesmo que o tipo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0445f-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="0445f-106">O **Escopo** da configuração indica se a propriedade é somente leitura: a propriedade para uma configuração de escopo do **Aplicativo** é somente leitura, enquanto que a propriedade para uma configuração de escopo do **Usuário** é de leitura/gravação.</span><span class="sxs-lookup"><span data-stu-id="0445f-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="0445f-107">Para obter mais informações, consulte [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="0445f-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0445f-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0445f-108">Example</span></span>  

 <span data-ttu-id="0445f-109">Este exemplo exibe o valor da configuração `Nickname`.</span><span class="sxs-lookup"><span data-stu-id="0445f-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="0445f-110">Para que esse exemplo funcione, seu aplicativo deve ter uma configuração `Nickname`, do tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="0445f-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="0445f-111">Para obter mais informações, consulte [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="0445f-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0445f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0445f-112">See also</span></span>

- [<span data-ttu-id="0445f-113">Objeto My.Settings</span><span class="sxs-lookup"><span data-stu-id="0445f-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="0445f-114">Como alterar configurações do usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0445f-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="0445f-115">Como persistir configurações do usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0445f-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="0445f-116">Como criar grades de propriedades para configurações do usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0445f-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="0445f-117">Gerenciando configurações de aplicativo (.NET)</span><span class="sxs-lookup"><span data-stu-id="0445f-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
