---
ms.openlocfilehash: 4b5c886ad35afbbf0a68e03b3174ab9ea1f5524f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614291"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a><span data-ttu-id="0ada8-101">CspParameters.ParentWindowHandle agora espera o valor HWND</span><span class="sxs-lookup"><span data-stu-id="0ada8-101">CspParameters.ParentWindowHandle now expects HWND value</span></span>

#### <a name="details"></a><span data-ttu-id="0ada8-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="0ada8-102">Details</span></span>

<span data-ttu-id="0ada8-103">O valor <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle>, introduzido no .NET Framework 2.0, permite que um aplicativo registre um valor de identificador de janela pai, de modo que qualquer interface do usuário necessária para acessar a chave (por exemplo, uma caixa de diálogo de solicitação de PIN ou de consentimento) seja aberta como um filho modal para a janela especificada. A partir dos aplicativos destinados ao .NET Framework 4.7, um aplicativo do Windows Forms pode definir a propriedade <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> com código como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0ada8-103">The <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> value, introduced in .NET Framework 2.0, allows an application to register a parent window handle value such that any UI required to access the key (such as a PIN prompt or consent dialog) opens as a modal child to the specified window.Starting with apps that target the .NET Framework 4.7, a Windows Forms application can set the <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> property with code like the following:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

<span data-ttu-id="0ada8-104">Em versões anteriores do .NET Framework, esperava-se que o valor fosse um <xref:System.IntPtr?displayProperty=fullName> representando um local na memória em que o valor de [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) residia.</span><span class="sxs-lookup"><span data-stu-id="0ada8-104">In previous versions of the .NET Framework, the value was expected to be an <xref:System.IntPtr?displayProperty=fullName> representing a location in memory where the [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) value resided.</span></span> <span data-ttu-id="0ada8-105">Definir a propriedade como form.Handle no Windows 7 e em versões anteriores não tinha efeito. No Windows 8 e em versões posteriores, isso resulta em &quot;<xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>: O parâmetro está incorreto.&quot;</span><span class="sxs-lookup"><span data-stu-id="0ada8-105">Setting the property to form.Handle on Windows 7 and earlier versions had no effect, but on Windows 8 and later versions, it results in a &quot;<xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>: The parameter is incorrect.&quot;</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0ada8-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="0ada8-106">Suggestion</span></span>

<span data-ttu-id="0ada8-107">Os aplicativos direcionados ao .NET Framework 4.7 ou posterior que desejam registrar um relacionamento de janela pai são incentivados a usar o formato simplificado:</span><span class="sxs-lookup"><span data-stu-id="0ada8-107">Applications targeting .NET Framework 4.7 or higher wishing to register a parent window relationship are encouraged to use the simplified form:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

<span data-ttu-id="0ada8-108">Usuários que identificaram que o valor correto a ser passado era o endereço de um local da memória que mantinha o valor de `form.Handle` podem recusar essa alteração de comportamento definindo o comutador AppContext `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` como `true`:</span><span class="sxs-lookup"><span data-stu-id="0ada8-108">Users who had identified that the correct value to pass was the address of a memory location which held the value `form.Handle` can opt out of the behavior change by setting the AppContext switch `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` to `true`:</span></span>

- <span data-ttu-id="0ada8-109">Configurando de forma programática as opções de compatibilidade em AppContext, conforme explicado [aqui](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span><span class="sxs-lookup"><span data-stu-id="0ada8-109">By programmatically setting compat switches on the AppContext, as explained [here](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span></span>
- <span data-ttu-id="0ada8-110">Adicionando a seguinte linha na seção `<runtime>` do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="0ada8-110">By adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<runtime>
 <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
</runtime>
```

<span data-ttu-id="0ada8-111">Por outro lado, usuários que quiserem aceitar o novo comportamento no runtime do .NET Framework 4.7 quando o aplicativo for carregado em versões anteriores do .NET Framework podem definir a opção de AppContext como `false`.</span><span class="sxs-lookup"><span data-stu-id="0ada8-111">Conversely, users who wish to opt in to the new behavior on the .NET Framework 4.7 runtime when the application loads under older .NET Framework versions can set the AppContext switch to `false`.</span></span>

| <span data-ttu-id="0ada8-112">Name</span><span class="sxs-lookup"><span data-stu-id="0ada8-112">Name</span></span>    | <span data-ttu-id="0ada8-113">Valor</span><span class="sxs-lookup"><span data-stu-id="0ada8-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0ada8-114">Escopo</span><span class="sxs-lookup"><span data-stu-id="0ada8-114">Scope</span></span>   | <span data-ttu-id="0ada8-115">Secundária</span><span class="sxs-lookup"><span data-stu-id="0ada8-115">Minor</span></span>       |
| <span data-ttu-id="0ada8-116">Versão</span><span class="sxs-lookup"><span data-stu-id="0ada8-116">Version</span></span> | <span data-ttu-id="0ada8-117">4.7</span><span class="sxs-lookup"><span data-stu-id="0ada8-117">4.7</span></span>         |
| <span data-ttu-id="0ada8-118">Type</span><span class="sxs-lookup"><span data-stu-id="0ada8-118">Type</span></span>    | <span data-ttu-id="0ada8-119">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="0ada8-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="0ada8-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0ada8-120">Affected APIs</span></span>

- <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType>
