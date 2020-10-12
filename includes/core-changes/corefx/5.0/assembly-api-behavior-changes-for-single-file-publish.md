---
ms.openlocfilehash: 0d6847b7a937094f36efae70ae450cc37824221d
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955545"
---
### <a name="assembly-related-api-behavior-changes-for-single-file-publishing-format"></a><span data-ttu-id="5a27c-101">Alterações de comportamento da API relacionadas ao assembly para o formato de publicação de arquivo único</span><span class="sxs-lookup"><span data-stu-id="5a27c-101">Assembly-related API behavior changes for single-file publishing format</span></span>

<span data-ttu-id="5a27c-102">Várias APIs relacionadas ao local do arquivo de um assembly têm alterações de comportamento quando são invocadas em um formato de publicação de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="5a27c-102">Multiple APIs related to an assembly's file location have behavior changes when they're invoked in a single-file publishing format.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5a27c-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="5a27c-103">Change description</span></span>

<span data-ttu-id="5a27c-104">Na publicação de arquivo único para .NET 5,0 e versões posteriores, os assemblies agrupados são carregados da memória, em vez de serem extraídos em disco.</span><span class="sxs-lookup"><span data-stu-id="5a27c-104">In single-file publishing for .NET 5.0 and later versions, bundled assemblies are loaded from memory instead of extracted to disk.</span></span> <span data-ttu-id="5a27c-105">Para aplicativos publicados de arquivo único, isso significa que determinadas APIs relacionadas ao local retornam valores diferentes no .NET 5,0 e posteriores do que nas versões anteriores do .NET.</span><span class="sxs-lookup"><span data-stu-id="5a27c-105">For single-file published apps, this means that certain location-related APIs return different values on .NET 5.0 and later than on previous versions of .NET.</span></span> <span data-ttu-id="5a27c-106">As alterações são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="5a27c-106">The changes are as follows:</span></span>

| <span data-ttu-id="5a27c-107">API</span><span class="sxs-lookup"><span data-stu-id="5a27c-107">API</span></span> | <span data-ttu-id="5a27c-108">Versões anteriores</span><span class="sxs-lookup"><span data-stu-id="5a27c-108">Previous versions</span></span> | <span data-ttu-id="5a27c-109">.NET 5,0 e posterior</span><span class="sxs-lookup"><span data-stu-id="5a27c-109">.NET 5.0 and later</span></span> |
| - | - | - |
| <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> | <span data-ttu-id="5a27c-110">Retorna o caminho do arquivo DLL extraído</span><span class="sxs-lookup"><span data-stu-id="5a27c-110">Returns extracted DLL file path</span></span> | <span data-ttu-id="5a27c-111">Retorna uma cadeia de caracteres vazia para assemblies agrupados</span><span class="sxs-lookup"><span data-stu-id="5a27c-111">Returns empty string for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> | <span data-ttu-id="5a27c-112">Retorna o caminho do arquivo DLL extraído</span><span class="sxs-lookup"><span data-stu-id="5a27c-112">Returns extracted DLL file path</span></span> | <span data-ttu-id="5a27c-113">Gera uma exceção para assemblies agrupados</span><span class="sxs-lookup"><span data-stu-id="5a27c-113">Throws exception for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType> | <span data-ttu-id="5a27c-114">Retorna `null` para assemblies agrupados</span><span class="sxs-lookup"><span data-stu-id="5a27c-114">Returns `null` for bundled assemblies</span></span> | <span data-ttu-id="5a27c-115">Gera uma exceção para assemblies agrupados</span><span class="sxs-lookup"><span data-stu-id="5a27c-115">Throws exception for bundled assemblies</span></span> |
| `Environment.GetCommandLineArgs()[0]` | <span data-ttu-id="5a27c-116">Valor é o nome da DLL do ponto de entrada</span><span class="sxs-lookup"><span data-stu-id="5a27c-116">Value is the name of the entry point DLL</span></span> | <span data-ttu-id="5a27c-117">Value é o nome do executável do host</span><span class="sxs-lookup"><span data-stu-id="5a27c-117">Value is the name of the host executable</span></span> |
| <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> | <span data-ttu-id="5a27c-118">O valor é o diretório de extração temporário</span><span class="sxs-lookup"><span data-stu-id="5a27c-118">Value is the temporary extraction directory</span></span> | <span data-ttu-id="5a27c-119">O valor é o diretório recipiente do executável do host</span><span class="sxs-lookup"><span data-stu-id="5a27c-119">Value is the containing directory of the host executable</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="5a27c-120">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="5a27c-120">Version introduced</span></span>

<span data-ttu-id="5a27c-121">5.0</span><span class="sxs-lookup"><span data-stu-id="5a27c-121">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5a27c-122">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="5a27c-122">Recommended action</span></span>

<span data-ttu-id="5a27c-123">Evite dependências no local do arquivo de assemblies ao publicar como um único arquivo.</span><span class="sxs-lookup"><span data-stu-id="5a27c-123">Avoid dependencies on the file location of assemblies when publishing as a single file.</span></span>

#### <a name="category"></a><span data-ttu-id="5a27c-124">Categoria</span><span class="sxs-lookup"><span data-stu-id="5a27c-124">Category</span></span>

- <span data-ttu-id="5a27c-125">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="5a27c-125">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5a27c-126">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="5a27c-126">Affected APIs</span></span>

- <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType>
- <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>
- <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Reflection.Assembly.Location`
- `P:System.Reflection.Assembly.CodeBase`
- `M:System.Reflection.Assembly.GetFile(System.String)`
- `M:System.Environment.GetCommandLineArgs`
- `P:System.AppContext.BaseDirectory`

-->
