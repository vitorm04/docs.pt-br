---
title: "Desenvolvimento rápido de aplicativos com My. Resources e My. Settings (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My.Settings object, developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object, developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
caps.latest.revision: 6
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
ms.openlocfilehash: 50fdcaf2b320574afa021efd4028da8d737932de
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="f1b4e-102">Desenvolvimento de aplicativo rápido com My.Resources e My.Settings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1b4e-102">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>
<span data-ttu-id="f1b4e-103">O `My.Resources` objeto fornece acesso aos recursos do aplicativo e permite que você se recupere dinamicamente recursos para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f1b4e-103">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="f1b4e-104">Recuperando recursos</span><span class="sxs-lookup"><span data-stu-id="f1b4e-104">Retrieving Resources</span></span>  
 <span data-ttu-id="f1b4e-105">Um número de recursos, como arquivos de áudio, ícones, imagens e cadeias de caracteres pode ser recuperado através de `My.Resources` objeto.</span><span class="sxs-lookup"><span data-stu-id="f1b4e-105">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="f1b4e-106">Por exemplo, você pode acessar arquivos de recurso com cultura específica do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f1b4e-106">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="f1b4e-107">O exemplo a seguir define o ícone do formulário para o ícone chamado `Form1Icon` armazenados no arquivo de recurso do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f1b4e-107">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 <span data-ttu-id="f1b4e-108">[!code-vb[VbVbcnMy&#7;](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f1b4e-108">[!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]</span></span>  
  
 <span data-ttu-id="f1b4e-109">O `My.Resources` objeto expõe apenas recursos globais.</span><span class="sxs-lookup"><span data-stu-id="f1b4e-109">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="f1b4e-110">Ele não fornece acesso aos arquivos de recursos associados a formulários.</span><span class="sxs-lookup"><span data-stu-id="f1b4e-110">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="f1b4e-111">Você deve acessar os recursos de formulário do formulário.</span><span class="sxs-lookup"><span data-stu-id="f1b4e-111">You must access the form resources from the form.</span></span> <span data-ttu-id="f1b4e-112">Para obter mais informações, consulte [Passo a passo: Localizando o Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).</span><span class="sxs-lookup"><span data-stu-id="f1b4e-112">For more information, see [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).</span></span>  
  
 <span data-ttu-id="f1b4e-113">Da mesma forma, o `My.Settings` objeto fornece acesso às configurações do aplicativo e permite que você armazene dinamicamente e recupere as configurações de propriedade e outras informações para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f1b4e-113">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="f1b4e-114">Para obter mais informações, consulte [objeto My. Resources](../../../visual-basic/language-reference/objects/my-resources-object.md) e [objeto My. Settings](../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="f1b4e-114">For more information, see [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) and [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1b4e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1b4e-115">See Also</span></span>  
 <span data-ttu-id="f1b4e-116">[Objeto My. Resources](../../../visual-basic/language-reference/objects/my-resources-object.md) </span><span class="sxs-lookup"><span data-stu-id="f1b4e-116">[My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) </span></span>  
<span data-ttu-id="f1b4e-117"> [Objeto My. Settings](../../../visual-basic/language-reference/objects/my-settings-object.md) </span><span class="sxs-lookup"><span data-stu-id="f1b4e-117"> [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md) </span></span>  
<span data-ttu-id="f1b4e-118"> [Acessando configurações de aplicativo](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f1b4e-118"> [Accessing Application Settings](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)</span></span>
