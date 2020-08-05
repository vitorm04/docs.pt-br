---
ms.openlocfilehash: 74c3d3247912dcd638a9379d54e682967c5e400b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302693"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a><span data-ttu-id="43027-101">APIs de globalização usam bibliotecas ICU no Windows</span><span class="sxs-lookup"><span data-stu-id="43027-101">Globalization APIs use ICU libraries on Windows</span></span>

<span data-ttu-id="43027-102">O .NET 5,0 e versões posteriores usam bibliotecas [internacionais para](http://site.icu-project.org/home) a funcionalidade de globalização na execução no Windows 10 pode ser 2019 atualização ou posterior.</span><span class="sxs-lookup"><span data-stu-id="43027-102">.NET 5.0 and later versions use [International Components for Unicode (ICU)](http://site.icu-project.org/home) libraries for globalization functionality when running on Windows 10 May 2019 Update or later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="43027-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="43027-103">Change description</span></span>

<span data-ttu-id="43027-104">Anteriormente, as bibliotecas do .NET usavam APIs [NLS (suporte a idioma nacional)](/windows/win32/intl/national-language-support) para a funcionalidade de globalização.</span><span class="sxs-lookup"><span data-stu-id="43027-104">Previously, .NET libraries used [National Language Support (NLS)](/windows/win32/intl/national-language-support) APIs for globalization functionality.</span></span> <span data-ttu-id="43027-105">Por exemplo, as funções NLS foram usadas para obter dados de cultura, como padrões de formato de data e hora, comparar cadeias de caracteres e executar maiúsculas e minúsculas na cultura apropriada.</span><span class="sxs-lookup"><span data-stu-id="43027-105">For example, NLS functions were used to get culture data, such as date and time format patterns, compare strings, and perform string casing in the appropriate culture.</span></span>

<span data-ttu-id="43027-106">A partir do .NET 5,0, se um aplicativo estiver em execução no Windows 10 pode ser 2019 Update ou posterior, as bibliotecas do .NET usarão APIs de globalização [ICU](http://site.icu-project.org/home) .</span><span class="sxs-lookup"><span data-stu-id="43027-106">Starting in .NET 5.0, if an app is running on Windows 10 May 2019 Update or later, .NET libraries use [ICU](http://site.icu-project.org/home) globalization APIs.</span></span> <span data-ttu-id="43027-107">O Windows 10 pode 2019 atualização e versões posteriores são fornecidas com a biblioteca nativa do ICU.</span><span class="sxs-lookup"><span data-stu-id="43027-107">Windows 10 May 2019 Update and later versions ship with the ICU native library.</span></span> <span data-ttu-id="43027-108">Se o tempo de execução do .NET não puder carregar o ICU, ele usará o NLS.</span><span class="sxs-lookup"><span data-stu-id="43027-108">If the .NET runtime can't load ICU, it uses NLS instead.</span></span>

<span data-ttu-id="43027-109">Essa alteração foi introduzida por dois motivos:</span><span class="sxs-lookup"><span data-stu-id="43027-109">This change was introduced for two reasons:</span></span>

- <span data-ttu-id="43027-110">Os aplicativos têm o mesmo comportamento de globalização entre as plataformas, incluindo Linux, macOS e Windows.</span><span class="sxs-lookup"><span data-stu-id="43027-110">Apps have the same globalization behavior across platforms, including Linux, macOS, and Windows.</span></span>
- <span data-ttu-id="43027-111">Os aplicativos podem controlar o comportamento de globalização usando bibliotecas ICU personalizadas.</span><span class="sxs-lookup"><span data-stu-id="43027-111">Apps can control globalization behavior by using custom ICU libraries.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="43027-112">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="43027-112">Version introduced</span></span>

<span data-ttu-id="43027-113">.NET 5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="43027-113">.NET 5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="43027-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="43027-114">Recommended action</span></span>

<span data-ttu-id="43027-115">Nenhuma ação é necessária na parte do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="43027-115">No action is required on the part of the developer.</span></span> <span data-ttu-id="43027-116">No entanto, se você quiser continuar usando as APIs de globalização NLS, poderá definir uma [opção de tempo de execução](../../../../docs/core/run-time-config/globalization.md#nls) para reverter para esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="43027-116">However, if you wish to continue using NLS globalization APIs, you can set a [run-time switch](../../../../docs/core/run-time-config/globalization.md#nls) to revert to that behavior.</span></span> <span data-ttu-id="43027-117">Para obter mais informações sobre as opções disponíveis, consulte o artigo [globalização .net e ICU](/dotnet/standard/globalization-localization/globalization-icu) .</span><span class="sxs-lookup"><span data-stu-id="43027-117">For more information about the available switches, see the [.NET globalization and ICU](/dotnet/standard/globalization-localization/globalization-icu) article.</span></span>

#### <a name="category"></a><span data-ttu-id="43027-118">Categoria</span><span class="sxs-lookup"><span data-stu-id="43027-118">Category</span></span>

<span data-ttu-id="43027-119">Globalização</span><span class="sxs-lookup"><span data-stu-id="43027-119">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="43027-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="43027-120">Affected APIs</span></span>

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <span data-ttu-id="43027-121">Maioria dos tipos no <xref:System.Globalization?displayProperty=fullName> namespace</span><span class="sxs-lookup"><span data-stu-id="43027-121">Most types in the <xref:System.Globalization?displayProperty=fullName> namespace</span></span>

<!--

#### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`

-->
