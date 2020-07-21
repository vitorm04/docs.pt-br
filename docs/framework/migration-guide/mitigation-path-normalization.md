---
title: 'Mitigação: normalização do caminho'
description: Saiba como a normalização de caminho no .NET Framework foi alterada começando com aplicativos direcionados .NET Framework 4.6.2.
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 89dcc46d9f266ffd3635dc0cc02b634720356eda
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475210"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="ea5ac-103">Mitigação: normalização do caminho</span><span class="sxs-lookup"><span data-stu-id="ea5ac-103">Mitigation: Path Normalization</span></span>
<span data-ttu-id="ea5ac-104">A partir de aplicativos direcionados .NET Framework 4.6.2, a normalização de caminho no .NET Framework foi alterada.</span><span class="sxs-lookup"><span data-stu-id="ea5ac-104">Starting with apps that target .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="ea5ac-105">O que é normalização do caminho?</span><span class="sxs-lookup"><span data-stu-id="ea5ac-105">What is path normalization?</span></span>  
 <span data-ttu-id="ea5ac-106">Normalizar um caminho envolve modificar a cadeia de caracteres que identifica um caminho ou arquivo para que ele esteja em conformidade com um caminho válido no sistema operacional de destino.</span><span class="sxs-lookup"><span data-stu-id="ea5ac-106">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="ea5ac-107">Normalmente, a normalização envolve:</span><span class="sxs-lookup"><span data-stu-id="ea5ac-107">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="ea5ac-108">Padronização de separadores de diretório e componente.</span><span class="sxs-lookup"><span data-stu-id="ea5ac-108">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="ea5ac-109">Aplicação do diretório atual a um caminho relativo.</span><span class="sxs-lookup"><span data-stu-id="ea5ac-109">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="ea5ac-110">Avaliação do diretório relativo (`.`) ou do diretório pai (`..`) em um caminho.</span><span class="sxs-lookup"><span data-stu-id="ea5ac-110">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="ea5ac-111">Remoção de determinados caracteres.</span><span class="sxs-lookup"><span data-stu-id="ea5ac-111">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="ea5ac-112">As alterações</span><span class="sxs-lookup"><span data-stu-id="ea5ac-112">The changes</span></span>  
 <span data-ttu-id="ea5ac-113">Começando com os aplicativos direcionados ao .NET Framework 4.6.2, a normalização do caminho foi alterada nos seguintes aspectos:</span><span class="sxs-lookup"><span data-stu-id="ea5ac-113">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="ea5ac-114">O runtime atende à função [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) do sistema operacional para normalizar caminhos.</span><span class="sxs-lookup"><span data-stu-id="ea5ac-114">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="ea5ac-115">A normalização não envolve mais a remoção do fim dos segmentos do diretório (como um espaço no fim do nome de um diretório).</span><span class="sxs-lookup"><span data-stu-id="ea5ac-115">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="ea5ac-116">Suporte à sintaxe do caminho do dispositivo em confiança total, incluindo `\\.\` e, para APIs de E/S de arquivo em mscorlib.dll, `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="ea5ac-116">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="ea5ac-117">O runtime não valida caminhos de sintaxe do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ea5ac-117">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="ea5ac-118">Há suporte ao uso da sintaxe de dispositivo para acessar fluxos de dados alternados.</span><span class="sxs-lookup"><span data-stu-id="ea5ac-118">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="ea5ac-119">Impacto</span><span class="sxs-lookup"><span data-stu-id="ea5ac-119">Impact</span></span>  

<span data-ttu-id="ea5ac-120">Para os aplicativos direcionados ao .NET Framework 4.6.2 ou posterior, essas alterações estão ativadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="ea5ac-120">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="ea5ac-121">Elas devem melhorar o desempenho e ao mesmo tempo permitir que os métodos acessem caminhos anteriormente inacessíveis.</span><span class="sxs-lookup"><span data-stu-id="ea5ac-121">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="ea5ac-122">Os aplicativos direcionados ao .NET Framework 4.6.1 e versões anteriores, mas que são executados no .NET Framework 4.6.2 ou posteriores, não são afetados por essa alteração.</span><span class="sxs-lookup"><span data-stu-id="ea5ac-122">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="ea5ac-123">Atenuação</span><span class="sxs-lookup"><span data-stu-id="ea5ac-123">Mitigation</span></span>  
 <span data-ttu-id="ea5ac-124">Os aplicativos que visam o .NET Framework 4.6.2 ou posterior podem recusar essa alteração e usar a normalização herdada adicionando o seguinte à [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) seção do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ea5ac-124">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
<span data-ttu-id="ea5ac-125">Aplicativos direcionados para o .NET Framework 4.6.1 ou anterior, mas que estão em execução no .NET Framework 4.6.2 ou posterior podem habilitar as alterações na normalização de caminho adicionando a seguinte linha à [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) seção do arquivo Application. Configuration:</span><span class="sxs-lookup"><span data-stu-id="ea5ac-125">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea5ac-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea5ac-126">See also</span></span>

- [<span data-ttu-id="ea5ac-127">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="ea5ac-127">Application compatibility</span></span>](application-compatibility.md)
