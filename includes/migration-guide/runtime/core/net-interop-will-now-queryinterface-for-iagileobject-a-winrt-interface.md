---
ms.openlocfilehash: 65fa5d8629ce8e426cf1623590a056e5cad0b91f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496321"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a><span data-ttu-id="ecbe9-101">A Interoperabilidade do .NET agora fará QueryInterface para IAgileObject (uma interface do WinRT)</span><span class="sxs-lookup"><span data-stu-id="ecbe9-101">.NET Interop will now QueryInterface for IAgileObject (a WinRT interface)</span></span>

#### <a name="details"></a><span data-ttu-id="ecbe9-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ecbe9-102">Details</span></span>

<span data-ttu-id="ecbe9-103">Ao usar um evento de WinRT com um delegado do .NET, Windows fará QI para IAgileObject começando com o .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="ecbe9-103">When using a WinRT event with a .NET delegate, Windows will QI for IAgileObject starting with the .NET Framework 4.8.</span></span>  <span data-ttu-id="ecbe9-104">Nas versões anteriores do .NET Framework, o runtime falharia nessa QI e o evento não poderia ser assinado.</span><span class="sxs-lookup"><span data-stu-id="ecbe9-104">In previous versions of the .NET Framework, the runtime would fail that QI, and the event could not be subscribed.</span></span><ul><li><span data-ttu-id="ecbe9-105">[x] Quirked</span><span class="sxs-lookup"><span data-stu-id="ecbe9-105">[ x ] Quirked</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="ecbe9-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ecbe9-106">Suggestion</span></span>

<span data-ttu-id="ecbe9-107">Se a habilitação de QI para IAgileObject interromper a execução, você poderá desabilitar esse código definindo a configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="ecbe9-107">If enabling the QI for IAgileObject breaks execution, you can disable this code by setting the following configuration.</span></span> <h4><span data-ttu-id="ecbe9-108">Método 1: variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="ecbe9-108">Method 1: Environment variable</span></span></h4> <span data-ttu-id="ecbe9-109">Defina a variável de ambiente a seguir:COMPLUS_DisableCCWSupportIAgileObject=1Esse método afeta qualquer ambiente que herda essa variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="ecbe9-109">Set the following environment variable:COMPLUS_DisableCCWSupportIAgileObject=1This method affects any environment that inherits this environment variable.</span></span> <span data-ttu-id="ecbe9-110">Isso pode ser apenas uma única sessão de console ou pode afetar o computador inteiro se você definir a variável de ambiente globalmente.</span><span class="sxs-lookup"><span data-stu-id="ecbe9-110">This might be just a single console session, or it might affect the entire machine if you set the environment variable globally.</span></span> <span data-ttu-id="ecbe9-111">O nome da variável de ambiente não diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="ecbe9-111">The environment variable name is not case-sensitive.</span></span> <h4><span data-ttu-id="ecbe9-112">Método 2: registro</span><span class="sxs-lookup"><span data-stu-id="ecbe9-112">Method 2: Registry</span></span></h4> <span data-ttu-id="ecbe9-113">Usando o editor do registro (regedit.exe), localize uma das seguintes subchaves: HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER \SOFTWARE\Microsoft.NETFrameworkThen adicione o seguinte: nome do valor: DisableCCWSupportIAgileObject tipo: DWORD (32-bit) valor (também chamado de REG_WORD) valor: 1Você pode usar a ferramenta de REG.EXE do Windows para adicionar esse valor de um ambiente de linha de comando ou de script.</span><span class="sxs-lookup"><span data-stu-id="ecbe9-113">Using Registry Editor (regedit.exe), find either of the following subkeys:HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER\SOFTWARE\Microsoft.NETFrameworkThen add the following:Value name: DisableCCWSupportIAgileObject Type: DWORD (32-bit) Value (also called REG_WORD) Value: 1You can use the Windows REG.EXE tool to add this value from a command-line or scripting environment.</span></span> <span data-ttu-id="ecbe9-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ecbe9-114">For example:</span></span><pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre><span data-ttu-id="ecbe9-115">Nesse caso, <code>HKLM</code> é usado em vez de <code>HKEY_LOCAL_MACHINE</code>.</span><span class="sxs-lookup"><span data-stu-id="ecbe9-115">In this case, <code>HKLM</code> is used instead of <code>HKEY_LOCAL_MACHINE</code>.</span></span> <span data-ttu-id="ecbe9-116">Use <code>reg add /?</code> para ver a ajuda nessa sintaxe.</span><span class="sxs-lookup"><span data-stu-id="ecbe9-116">Use <code>reg add /?</code> to see help on this syntax.</span></span> <span data-ttu-id="ecbe9-117">O nome do valor do registro não diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="ecbe9-117">The registry value name is not case-sensitive.</span></span>

| <span data-ttu-id="ecbe9-118">Nome</span><span class="sxs-lookup"><span data-stu-id="ecbe9-118">Name</span></span>    | <span data-ttu-id="ecbe9-119">Valor</span><span class="sxs-lookup"><span data-stu-id="ecbe9-119">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ecbe9-120">Escopo</span><span class="sxs-lookup"><span data-stu-id="ecbe9-120">Scope</span></span>   |<span data-ttu-id="ecbe9-121">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="ecbe9-121">Edge</span></span>|
|<span data-ttu-id="ecbe9-122">Versão</span><span class="sxs-lookup"><span data-stu-id="ecbe9-122">Version</span></span>|<span data-ttu-id="ecbe9-123">4.8</span><span class="sxs-lookup"><span data-stu-id="ecbe9-123">4.8</span></span>|
|<span data-ttu-id="ecbe9-124">Tipo</span><span class="sxs-lookup"><span data-stu-id="ecbe9-124">Type</span></span>|<span data-ttu-id="ecbe9-125">Runtime</span><span class="sxs-lookup"><span data-stu-id="ecbe9-125">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ecbe9-126">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ecbe9-126">Affected APIs</span></span>

<span data-ttu-id="ecbe9-127">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="ecbe9-127">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
