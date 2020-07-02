---
ms.openlocfilehash: 04c4fb4c8e9da8c58a5e26f78a7b13aa6a0df4a0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614278"
---
### <a name="changes-in-path-normalization"></a><span data-ttu-id="986d8-101">Alterações na normalização de caminho</span><span class="sxs-lookup"><span data-stu-id="986d8-101">Changes in path normalization</span></span>

#### <a name="details"></a><span data-ttu-id="986d8-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="986d8-102">Details</span></span>

<span data-ttu-id="986d8-103">A partir de aplicativos destinados ao .NET Framework 4.6.2, a maneira como o runtime normaliza caminhos foi alterada. Normalizar um caminho envolve modificar a cadeia de caracteres que identifica um arquivo ou caminho para que ela corresponda a um caminho válido no sistema operacional de destino.</span><span class="sxs-lookup"><span data-stu-id="986d8-103">Starting with apps that target the .NET Framework 4.6.2, the way in which the runtime normalizes paths has changed.Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="986d8-104">Normalmente, a normalização envolve:</span><span class="sxs-lookup"><span data-stu-id="986d8-104">Normalization typically involves:</span></span>

- <span data-ttu-id="986d8-105">Padronização de separadores de diretório e componente.</span><span class="sxs-lookup"><span data-stu-id="986d8-105">Canonicalizing component and directory separators.</span></span>
- <span data-ttu-id="986d8-106">Aplicação do diretório atual a um caminho relativo.</span><span class="sxs-lookup"><span data-stu-id="986d8-106">Applying the current directory to a relative path.</span></span>
- <span data-ttu-id="986d8-107">Avaliação do diretório relativo (.) ou do diretório pai (..) em um caminho.</span><span class="sxs-lookup"><span data-stu-id="986d8-107">Evaluating the relative directory (.) or the parent directory (..) in a path.</span></span>
- <span data-ttu-id="986d8-108">Remoção de determinados caracteres.</span><span class="sxs-lookup"><span data-stu-id="986d8-108">Trimming specified characters.</span></span>
<span data-ttu-id="986d8-109">A partir dos aplicativos destinados ao .NET Framework 4.6.2, as seguintes alterações na normalização do caminho são habilitadas por padrão:</span><span class="sxs-lookup"><span data-stu-id="986d8-109">Starting with apps that target the .NET Framework 4.6.2, the following changes in path normalization are enabled by default:</span></span>
  - <span data-ttu-id="986d8-110">O runtime atende à função [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) do sistema operacional para normalizar caminhos.</span><span class="sxs-lookup"><span data-stu-id="986d8-110">The runtime defers to the operating system's [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) function to normalize paths.</span></span>
- <span data-ttu-id="986d8-111">A normalização não envolve mais a remoção do fim dos segmentos do diretório (como um espaço no fim do nome de um diretório).</span><span class="sxs-lookup"><span data-stu-id="986d8-111">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>
- <span data-ttu-id="986d8-112">Suporte à sintaxe do caminho do dispositivo em confiança total, incluindo `\\.\` e, para APIs de E/S de arquivo em mscorlib.dll, `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="986d8-112">Support for device path syntax in full trust, including `\\.\` and, for file I/O APIs in mscorlib.dll, `\\?\`.</span></span>
- <span data-ttu-id="986d8-113">O runtime não valida caminhos de sintaxe do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="986d8-113">The runtime does not validate device syntax paths.</span></span>
- <span data-ttu-id="986d8-114">Há suporte ao uso da sintaxe de dispositivo para acessar fluxos de dados alternados.</span><span class="sxs-lookup"><span data-stu-id="986d8-114">The use of device syntax to access alternate data streams is supported.</span></span>
<span data-ttu-id="986d8-115">Essas alterações devem melhorar o desempenho e ao mesmo tempo permitir que os métodos acessem caminhos anteriormente inacessíveis.</span><span class="sxs-lookup"><span data-stu-id="986d8-115">These changes improve performance while allowing methods to access previously inaccessible paths.</span></span> <span data-ttu-id="986d8-116">Os aplicativos direcionados ao .NET Framework 4.6.1 e versões anteriores, mas que são executados no .NET Framework 4.6.2 ou posteriores, não são afetados por essa alteração.</span><span class="sxs-lookup"><span data-stu-id="986d8-116">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="986d8-117">Sugestão</span><span class="sxs-lookup"><span data-stu-id="986d8-117">Suggestion</span></span>

<span data-ttu-id="986d8-118">Aplicativos destinados ao .NET Framework 4.6.2 ou posteriores podem recusar essa alteração e usar a normalização herdada adicionando o seguinte à seção `<runtime>` do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="986d8-118">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>
```

<span data-ttu-id="986d8-119">Aplicativos destinados ao .NET Framework 4.6.1 ou anteriores, mas que são executados no .NET Framework 4.6.2 ou posteriores podem habilitar as alterações na normalização de caminho adicionando a seguinte linha à seção `<runtime>` do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="986d8-119">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>
```

| <span data-ttu-id="986d8-120">Name</span><span class="sxs-lookup"><span data-stu-id="986d8-120">Name</span></span>    | <span data-ttu-id="986d8-121">Valor</span><span class="sxs-lookup"><span data-stu-id="986d8-121">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="986d8-122">Escopo</span><span class="sxs-lookup"><span data-stu-id="986d8-122">Scope</span></span>   | <span data-ttu-id="986d8-123">Secundária</span><span class="sxs-lookup"><span data-stu-id="986d8-123">Minor</span></span>       |
| <span data-ttu-id="986d8-124">Versão</span><span class="sxs-lookup"><span data-stu-id="986d8-124">Version</span></span> | <span data-ttu-id="986d8-125">4.6.2</span><span class="sxs-lookup"><span data-stu-id="986d8-125">4.6.2</span></span>       |
| <span data-ttu-id="986d8-126">Type</span><span class="sxs-lookup"><span data-stu-id="986d8-126">Type</span></span>    | <span data-ttu-id="986d8-127">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="986d8-127">Retargeting</span></span> |
