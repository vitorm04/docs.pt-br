---
title: 'Como: Alterar configurações de usuário no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 3cf50f838124539dc774574cd1ad0b629d01a9ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688166"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a><span data-ttu-id="29c2a-102">Como: Alterar configurações de usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29c2a-102">How to: Change User Settings in Visual Basic</span></span>
<span data-ttu-id="29c2a-103">Você pode alterar uma configuração do usuário atribuindo um novo valor à propriedade da configuração no objeto `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="29c2a-103">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="29c2a-104">O objeto `My.Settings` expõe cada configuração como uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="29c2a-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="29c2a-105">O nome da propriedade é o mesmo que o nome da configuração e o tipo de propriedade é o mesmo que o tipo de configuração.</span><span class="sxs-lookup"><span data-stu-id="29c2a-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="29c2a-106">O **Escopo** da configuração determina se a propriedade é somente leitura: A propriedade de uma configuração no escopo do **Aplicativo** é somente leitura, enquanto a propriedade de uma configuração no escopo do **Usuário** é leitura/gravação.</span><span class="sxs-lookup"><span data-stu-id="29c2a-106">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="29c2a-107">Para obter mais informações, consulte [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="29c2a-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29c2a-108">Embora você possa alterar e salvar os valores das configurações de escopo do usuário em tempo de execução, as configurações de escopo do aplicativo são somente leitura e não podem ser alteradas programaticamente.</span><span class="sxs-lookup"><span data-stu-id="29c2a-108">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="29c2a-109">Você pode alterar as configurações de escopo do aplicativo ao criar o aplicativo usando o **Designer de Projeto** ou editando o arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="29c2a-109">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span></span> <span data-ttu-id="29c2a-110">Para obter mais informações, consulte [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="29c2a-110">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="29c2a-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="29c2a-111">Example</span></span>  
 <span data-ttu-id="29c2a-112">Este exemplo altera o valor da configuração do usuário `Nickname`.</span><span class="sxs-lookup"><span data-stu-id="29c2a-112">This example changes the value of the `Nickname` user setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#7](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-change-user-settings_1.vb)]  
  
 <span data-ttu-id="29c2a-113">Para que esse exemplo funcione, seu aplicativo deve ter uma configuração do usuário `Nickname`, do tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="29c2a-113">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span></span>  
  
 <span data-ttu-id="29c2a-114">O aplicativo salva as configurações do usuário quando o aplicativo é desligado.</span><span class="sxs-lookup"><span data-stu-id="29c2a-114">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="29c2a-115">Para salvar as configurações imediatamente, chame o método `My.Settings.Save`.</span><span class="sxs-lookup"><span data-stu-id="29c2a-115">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="29c2a-116">Para obter mais informações, confira [Como: Persistir configurações de usuário em Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="29c2a-116">For more information, see [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29c2a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29c2a-117">See also</span></span>
- [<span data-ttu-id="29c2a-118">Objeto My.Settings</span><span class="sxs-lookup"><span data-stu-id="29c2a-118">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="29c2a-119">Como: ler configurações do aplicativo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29c2a-119">How to: Read Application Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="29c2a-120">Como: persistir configurações de usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29c2a-120">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="29c2a-121">Como: criar grades de propriedades para configurações do usuário no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29c2a-121">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="29c2a-122">Gerenciando configurações de aplicativo (.NET)</span><span class="sxs-lookup"><span data-stu-id="29c2a-122">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
