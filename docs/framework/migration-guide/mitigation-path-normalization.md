---
title: 'Mitigação: normalização do caminho'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 1e7b540975b84320d099ca004df5b6a87aa60f6a
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457889"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="ac49b-102">Mitigação: normalização do caminho</span><span class="sxs-lookup"><span data-stu-id="ac49b-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="ac49b-103">Começando com os aplicativos direcionados ao .NET Framework 4.6.2, a normalização do caminho no .NET Framework foi alterada.</span><span class="sxs-lookup"><span data-stu-id="ac49b-103">Starting with apps the target  the .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="ac49b-104">O que é normalização do caminho?</span><span class="sxs-lookup"><span data-stu-id="ac49b-104">What is path normalization?</span></span>  
 <span data-ttu-id="ac49b-105">Normalizar um caminho envolve modificar a cadeia de caracteres que identifica um caminho ou arquivo para que ele esteja em conformidade com um caminho válido no sistema operacional de destino.</span><span class="sxs-lookup"><span data-stu-id="ac49b-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="ac49b-106">Normalmente, a normalização envolve:</span><span class="sxs-lookup"><span data-stu-id="ac49b-106">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="ac49b-107">Padronização de separadores de diretório e componente.</span><span class="sxs-lookup"><span data-stu-id="ac49b-107">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="ac49b-108">Aplicação do diretório atual a um caminho relativo.</span><span class="sxs-lookup"><span data-stu-id="ac49b-108">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="ac49b-109">Avaliação do diretório relativo (`.`) ou do diretório pai (`..`) em um caminho.</span><span class="sxs-lookup"><span data-stu-id="ac49b-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="ac49b-110">Remoção de determinados caracteres.</span><span class="sxs-lookup"><span data-stu-id="ac49b-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="ac49b-111">As alterações</span><span class="sxs-lookup"><span data-stu-id="ac49b-111">The changes</span></span>  
 <span data-ttu-id="ac49b-112">Começando com os aplicativos direcionados ao .NET Framework 4.6.2, a normalização do caminho foi alterada nos seguintes aspectos:</span><span class="sxs-lookup"><span data-stu-id="ac49b-112">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="ac49b-113">O runtime atende à função [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) do sistema operacional para normalizar caminhos.</span><span class="sxs-lookup"><span data-stu-id="ac49b-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="ac49b-114">A normalização não envolve mais a remoção do fim dos segmentos do diretório (como um espaço no fim do nome de um diretório).</span><span class="sxs-lookup"><span data-stu-id="ac49b-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="ac49b-115">Suporte à sintaxe do caminho do dispositivo em confiança total, incluindo `\\.\` e, para APIs de E/S de arquivo em mscorlib.dll, `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="ac49b-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="ac49b-116">O runtime não valida caminhos de sintaxe do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ac49b-116">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="ac49b-117">Há suporte ao uso da sintaxe de dispositivo para acessar fluxos de dados alternados.</span><span class="sxs-lookup"><span data-stu-id="ac49b-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="ac49b-118">Impacto</span><span class="sxs-lookup"><span data-stu-id="ac49b-118">Impact</span></span>  

<span data-ttu-id="ac49b-119">Para os aplicativos direcionados ao .NET Framework 4.6.2 ou posterior, essas alterações estão ativadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="ac49b-119">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="ac49b-120">Elas devem melhorar o desempenho e ao mesmo tempo permitir que os métodos acessem caminhos anteriormente inacessíveis.</span><span class="sxs-lookup"><span data-stu-id="ac49b-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="ac49b-121">Os aplicativos direcionados ao .NET Framework 4.6.1 e versões anteriores, mas que são executados no .NET Framework 4.6.2 ou posteriores, não são afetados por essa alteração.</span><span class="sxs-lookup"><span data-stu-id="ac49b-121">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="ac49b-122">Redução</span><span class="sxs-lookup"><span data-stu-id="ac49b-122">Mitigation</span></span>  
 <span data-ttu-id="ac49b-123">Aplicativos destinados ao .NET Framework 4.6.2 ou posteriores podem recusar essa alteração e usar a normalização herdada adicionando o seguinte à seção [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ac49b-123">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
<span data-ttu-id="ac49b-124">Aplicativos destinados ao .NET Framework 4.6.1 ou anteriores, mas que são executados no .NET Framework 4.6.2 ou posteriores podem habilitar as alterações na normalização de caminho adicionando a seguinte linha à seção [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ac49b-124">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac49b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac49b-125">See also</span></span>

- [<span data-ttu-id="ac49b-126">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="ac49b-126">Application compatibility</span></span>](application-compatibility.md)
