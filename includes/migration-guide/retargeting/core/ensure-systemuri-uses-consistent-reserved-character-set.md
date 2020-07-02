---
ms.openlocfilehash: 21921156295d89aad04f3197fef9fa322f3c8c87
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614274"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a><span data-ttu-id="c5a26-101">Verifique se o System.URI usa um conjunto consistente de caracteres reservados</span><span class="sxs-lookup"><span data-stu-id="c5a26-101">Ensure System.Uri uses a consistent reserved character set</span></span>

#### <a name="details"></a><span data-ttu-id="c5a26-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c5a26-102">Details</span></span>

<span data-ttu-id="c5a26-103">No <xref:System.Uri?displayProperty=fullName>, determinados caracteres codificados por porcentagem que, às vezes, eram decodificados agora permanecem codificados de forma consistente.</span><span class="sxs-lookup"><span data-stu-id="c5a26-103">In <xref:System.Uri?displayProperty=fullName>, certain percent-encoded characters that were sometimes decoded are now consistently left encoded.</span></span> <span data-ttu-id="c5a26-104">Isso ocorre nas propriedades e nos métodos que acessam os componentes de caminho, consulta, fragmento ou informações do usuário do URI.</span><span class="sxs-lookup"><span data-stu-id="c5a26-104">This occurs across the properties and methods that access the path, query, fragment, or userinfo components of the URI.</span></span> <span data-ttu-id="c5a26-105">O comportamento será alterado somente quando os dois itens a seguir forem verdadeiros:</span><span class="sxs-lookup"><span data-stu-id="c5a26-105">The behavior will change only when both of the following are true:</span></span>

- <span data-ttu-id="c5a26-106">O URI contiver a forma codificada de um dos seguintes caracteres reservados: `:`, `'`, `(`, `)`, `!` ou `*`.</span><span class="sxs-lookup"><span data-stu-id="c5a26-106">The URI contains the encoded form of any of the following reserved characters: `:`, `'`, `(`, `)`, `!` or `*`.</span></span>
- <span data-ttu-id="c5a26-107">O URI contiver um caractere Unicode ou não reservado codificado.</span><span class="sxs-lookup"><span data-stu-id="c5a26-107">The URI contains a Unicode or encoded non-reserved character.</span></span> <span data-ttu-id="c5a26-108">Se ambas as condições acima forem verdadeiras, os caracteres reservados codificados serão deixados codificados.</span><span class="sxs-lookup"><span data-stu-id="c5a26-108">If both of the above are true, the encoded reserved characters are left encoded.</span></span> <span data-ttu-id="c5a26-109">Nas versões anteriores do .NET Framework, eles são decodificados.</span><span class="sxs-lookup"><span data-stu-id="c5a26-109">In previous versions of the .NET Framework, they are decoded.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c5a26-110">Sugestão</span><span class="sxs-lookup"><span data-stu-id="c5a26-110">Suggestion</span></span>

<span data-ttu-id="c5a26-111">Para aplicativos direcionados a versões do .NET Framework começando com a 4.7.2, o novo comportamento de decodificação é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="c5a26-111">For applications that target versions of .NET Framework starting with 4.7.2, the new decoding behavior is enabled by default.</span></span> <span data-ttu-id="c5a26-112">Se essa alteração não for desejada, você poderá desabilitá-la adicionando a seguinte opção [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) à seção `<runtime>` do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="c5a26-112">If this change is undesirable, you can disable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true" />
</runtime>
```

<span data-ttu-id="c5a26-113">Para aplicativos direcionados a versões anteriores do .NET Framework, mas executados em versões começando com o .NET Framework 4.7.2, o novo comportamento de decodificação é desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="c5a26-113">For applications that target earlier versions of the .NET Framework but are running under versions starting with .NET Framework 4.7.2, the new decoding behavior is disabled by default.</span></span> <span data-ttu-id="c5a26-114">Você pode habilitá-lo adicionando o seguinte comutador [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) à `<runtime>` seção do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="c5a26-114">You can enable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false" />
</runtime>
```

| <span data-ttu-id="c5a26-115">Name</span><span class="sxs-lookup"><span data-stu-id="c5a26-115">Name</span></span>    | <span data-ttu-id="c5a26-116">Valor</span><span class="sxs-lookup"><span data-stu-id="c5a26-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c5a26-117">Escopo</span><span class="sxs-lookup"><span data-stu-id="c5a26-117">Scope</span></span>   | <span data-ttu-id="c5a26-118">Secundária</span><span class="sxs-lookup"><span data-stu-id="c5a26-118">Minor</span></span>       |
| <span data-ttu-id="c5a26-119">Versão</span><span class="sxs-lookup"><span data-stu-id="c5a26-119">Version</span></span> | <span data-ttu-id="c5a26-120">4.7.2</span><span class="sxs-lookup"><span data-stu-id="c5a26-120">4.7.2</span></span>       |
| <span data-ttu-id="c5a26-121">Type</span><span class="sxs-lookup"><span data-stu-id="c5a26-121">Type</span></span>    | <span data-ttu-id="c5a26-122">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="c5a26-122">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c5a26-123">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="c5a26-123">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
