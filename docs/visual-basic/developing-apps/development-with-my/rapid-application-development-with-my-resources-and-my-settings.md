---
title: Desenvolvimento de aplicativo rápido com My.Resources e My.Settings (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 808e02510d4f0a237ad4354b2edac8fa024b5f83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="16035-102">Desenvolvimento de aplicativo rápido com My.Resources e My.Settings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16035-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>
<span data-ttu-id="16035-103">O `My.Resources` objeto fornece acesso aos recursos do aplicativo e permite que você recupere dinamicamente recursos para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="16035-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="16035-104">Recuperando recursos</span><span class="sxs-lookup"><span data-stu-id="16035-104">Retrieving Resources</span></span>  
 <span data-ttu-id="16035-105">Um número de recursos, como arquivos de áudio, ícones, imagens e cadeias de caracteres pode ser recuperado por meio de `My.Resources` objeto.</span><span class="sxs-lookup"><span data-stu-id="16035-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="16035-106">Por exemplo, você pode acessar arquivos de recursos específicos de cultura do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="16035-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="16035-107">O exemplo a seguir define o ícone do formulário para o ícone chamado `Form1Icon` armazenados no arquivo de recurso do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="16035-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 <span data-ttu-id="16035-108">O `My.Resources` objeto expõe apenas recursos globais.</span><span class="sxs-lookup"><span data-stu-id="16035-108">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="16035-109">Ele não fornece acesso aos arquivos de recursos associados a formulários.</span><span class="sxs-lookup"><span data-stu-id="16035-109">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="16035-110">Você deve acessar os recursos de formulário do formulário.</span><span class="sxs-lookup"><span data-stu-id="16035-110">You must access the form resources from the form.</span></span>  
  
 <span data-ttu-id="16035-111">Da mesma forma, o `My.Settings` objeto fornece acesso às configurações do aplicativo e permite que você armazene dinamicamente e recupere as configurações de propriedade e outras informações para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="16035-111">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="16035-112">Para obter mais informações, consulte [objeto My. Resources](../../../visual-basic/language-reference/objects/my-resources-object.md) e [objeto My. Settings](../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="16035-112">For more information, see [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) and [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16035-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16035-113">See Also</span></span>  
 [<span data-ttu-id="16035-114">Objeto My.Resources</span><span class="sxs-lookup"><span data-stu-id="16035-114">My.Resources Object</span></span>](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [<span data-ttu-id="16035-115">Objeto My.Settings</span><span class="sxs-lookup"><span data-stu-id="16035-115">My.Settings Object</span></span>](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [<span data-ttu-id="16035-116">Acessando configurações de aplicativo</span><span class="sxs-lookup"><span data-stu-id="16035-116">Accessing Application Settings</span></span>](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)
