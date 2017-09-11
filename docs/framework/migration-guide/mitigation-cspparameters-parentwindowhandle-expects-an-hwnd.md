---
title: "Mitigação: CspParameters.ParentWindowHandle espera um HWND"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- CspParameters.ParentWindowHandle
- CspParameters.ParentWindowHandle retargeting change
ms.assetid: 33264333-71d6-4d43-8827-9c98878cfea7
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1b65aaf7149ca29b2af3efdf44ee9489a04c73a2
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-cspparametersparentwindowhandle-expects-an-hwnd"></a><span data-ttu-id="3c05d-102">Mitigação: CspParameters.ParentWindowHandle espera um HWND</span><span class="sxs-lookup"><span data-stu-id="3c05d-102">Mitigation: CspParameters.ParentWindowHandle Expects an HWND</span></span>

<span data-ttu-id="3c05d-103">A propriedade <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A>, introduzida no .NET Framework 2.0, permite que um aplicativo registre um valor de identificador de janela pai, de modo que qualquer interface do usuário necessária para acessar a chave (por exemplo, uma caixa de diálogo de solicitação de PIN ou de consentimento) seja aberta como um filho modal para a janela especificada.</span><span class="sxs-lookup"><span data-stu-id="3c05d-103">The <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> property, introduced in the .NET Framework 2.0, allows an application to register a parent window handle value such that any UI required to access the key (such as a PIN prompt or a consent dialog) opens as a modal child to the specified window.</span></span> <span data-ttu-id="3c05d-104">Em aplicativos destinados ao .NET Framework 4.7, um identificador de janela (HWND) pode ser atribuído a essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="3c05d-104">Starting with applications that target the .NET Framework 4.7, a window handle (HWND) can be assigned to this property.</span></span>

<span data-ttu-id="3c05d-105">Nas versões do .NET Framework até o .NET Framework 4.6.2, esperava-se que o valor atribuído à propriedade <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> fosse um <xref:System.IntPtr> que representasse o local na memória no qual o valor de HWND residia.</span><span class="sxs-lookup"><span data-stu-id="3c05d-105">In versions of the .NET Framework through the .NET Framework 4.6.2, the value assigned to the <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> property was expected to be an <xref:System.IntPtr> that represents the location in memory where the HWND value resided.</span></span> <span data-ttu-id="3c05d-106">No Windows 7 e nas versões anteriores do sistema operacional Windows, definir a propriedade como `form.Handle` não tinha efeito, mas no Windows 8 e nas versões posteriores, isso resulta em uma <xref:System.Security.Cryptography> com a mensagem "O parâmetro está incorreto".</span><span class="sxs-lookup"><span data-stu-id="3c05d-106">On Windows 7 and earlier versions of the Windows operating system, setting the property to `form.Handle` had no effect, but on Windows 8 and later versions, it results in a <xref:System.Security.Cryptography> with the message, "The parameter is incorrect."</span></span>

<span data-ttu-id="3c05d-107">A partir dos aplicativos destinados ao .NET Framework 4.7, um aplicativo do Windows Forms pode definir a propriedade <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> com um código semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="3c05d-107">Starting with apps that target the .NET Framework 4.7, a Windows Forms application can set the <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle%2A> property with code like the following:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
``` 

## <a name="impact"></a><span data-ttu-id="3c05d-108">Impacto</span><span class="sxs-lookup"><span data-stu-id="3c05d-108">Impact</span></span>

<span data-ttu-id="3c05d-109">Os aplicativos destinados ao .NET Framework 4.7 ou posterior que desejam registrar um relacionamento de janela pai são incentivados a usar o formulário simplificado:</span><span class="sxs-lookup"><span data-stu-id="3c05d-109">Applications targeting the .NET Framework 4.7 or later that wish to register a parent window relationship are encouraged to use the simplified form:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
``` 

## <a name="mitigation"></a><span data-ttu-id="3c05d-110">Redução</span><span class="sxs-lookup"><span data-stu-id="3c05d-110">Mitigation</span></span>

<span data-ttu-id="3c05d-111">Os desenvolvedores que identificaram que o valor correto era o endereço do local da memória que mantinha o valor de `form.Handle` podem optar por não aceitar essa alteração de comportamento, definindo a opção de <xref:System.AppContext> `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` para `true`:</span><span class="sxs-lookup"><span data-stu-id="3c05d-111">Developers who had identified that the correct value was the address of the memory location that held the `form.Handle` value can opt out of this change in behavior by setting the <xref:System.AppContext> switch `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` to `true`:</span></span>

- <span data-ttu-id="3c05d-112">Configurando de forma programática as opções de compatibilidade na instância <xref:System.AppContext>.</span><span class="sxs-lookup"><span data-stu-id="3c05d-112">By programmatically setting compatibility switches on the <xref:System.AppContext> instance.</span></span>

- <span data-ttu-id="3c05d-113">Adicionando a seguinte linha na seção `<runtime>` do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="3c05d-113">By adding the following line to the `<runtime>` section of the app.config file:</span></span>
   
   ```xml
   <runtime>
     <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
   </runtime>
   ```

<span data-ttu-id="3c05d-114">Por outro lado, os usuários que desejam aceitar o novo comportamento para aplicativos que são executados no .NET Framework 4.7, mas que se destinam a uma versão anterior do .NET Framework, podem definir a opção de <xref:System.AppContext> para `false`.</span><span class="sxs-lookup"><span data-stu-id="3c05d-114">Conversely, users who wish to opt in to the new behavior for applications that run under the .NET Framework 4.7 but target an earlier version of the .NET Framework versions can set the <xref:System.AppContext> switch to `false`.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="3c05d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c05d-115">See also</span></span>

[<span data-ttu-id="3c05d-116">Alterações de redirecionamento no .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="3c05d-116">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

