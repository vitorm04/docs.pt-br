---
title: 'Mitigação: normalização do caminho'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 61c8eec2043aa2fb9309ee6052e27fc2c91c6c6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181232"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="23174-102">Mitigação: normalização do caminho</span><span class="sxs-lookup"><span data-stu-id="23174-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="23174-103">Começando com os aplicativos direcionados ao .NET Framework 4.6.2, a normalização do caminho no .NET Framework foi alterada.</span><span class="sxs-lookup"><span data-stu-id="23174-103">Starting with apps the target  the .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="23174-104">O que é normalização do caminho?</span><span class="sxs-lookup"><span data-stu-id="23174-104">What is path normalization?</span></span>  
 <span data-ttu-id="23174-105">Normalizar um caminho envolve modificar a cadeia de caracteres que identifica um caminho ou arquivo para que ele esteja em conformidade com um caminho válido no sistema operacional de destino.</span><span class="sxs-lookup"><span data-stu-id="23174-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="23174-106">Normalmente, a normalização envolve:</span><span class="sxs-lookup"><span data-stu-id="23174-106">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="23174-107">Padronização de separadores de diretório e componente.</span><span class="sxs-lookup"><span data-stu-id="23174-107">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="23174-108">Aplicação do diretório atual a um caminho relativo.</span><span class="sxs-lookup"><span data-stu-id="23174-108">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="23174-109">Avaliação do diretório relativo (`.`) ou do diretório pai (`..`) em um caminho.</span><span class="sxs-lookup"><span data-stu-id="23174-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="23174-110">Remoção de determinados caracteres.</span><span class="sxs-lookup"><span data-stu-id="23174-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="23174-111">As alterações</span><span class="sxs-lookup"><span data-stu-id="23174-111">The changes</span></span>  
 <span data-ttu-id="23174-112">Começando com os aplicativos direcionados ao .NET Framework 4.6.2, a normalização do caminho foi alterada nos seguintes aspectos:</span><span class="sxs-lookup"><span data-stu-id="23174-112">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="23174-113">O runtime atende à função [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) do sistema operacional para normalizar caminhos.</span><span class="sxs-lookup"><span data-stu-id="23174-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="23174-114">A normalização não envolve mais a remoção do fim dos segmentos do diretório (como um espaço no fim do nome de um diretório).</span><span class="sxs-lookup"><span data-stu-id="23174-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="23174-115">Suporte à sintaxe do caminho do dispositivo em confiança total, incluindo `\\.\` e, para APIs de E/S de arquivo em mscorlib.dll, `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="23174-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="23174-116">O runtime não valida caminhos de sintaxe do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="23174-116">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="23174-117">Há suporte ao uso da sintaxe de dispositivo para acessar fluxos de dados alternados.</span><span class="sxs-lookup"><span data-stu-id="23174-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="23174-118">Impacto</span><span class="sxs-lookup"><span data-stu-id="23174-118">Impact</span></span>  

<span data-ttu-id="23174-119">Para os aplicativos direcionados ao .NET Framework 4.6.2 ou posterior, essas alterações estão ativadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="23174-119">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="23174-120">Elas devem melhorar o desempenho e ao mesmo tempo permitir que os métodos acessem caminhos anteriormente inacessíveis.</span><span class="sxs-lookup"><span data-stu-id="23174-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="23174-121">Os aplicativos direcionados ao .NET Framework 4.6.1 e versões anteriores, mas que são executados no .NET Framework 4.6.2 ou posteriores, não são afetados por essa alteração.</span><span class="sxs-lookup"><span data-stu-id="23174-121">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="23174-122">Atenuação</span><span class="sxs-lookup"><span data-stu-id="23174-122">Mitigation</span></span>  
 <span data-ttu-id="23174-123">Os aplicativos que têm como alvo o .NET Framework 4.6.2 ou posterior escoam para desativar essa alteração e usar a normalização legado adicionando o [ \<](../configure-apps/file-schema/runtime/runtime-element.md) seguinte à seção de>em tempo de execução do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="23174-123">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
<span data-ttu-id="23174-124">Os aplicativos que têm como alvo o .NET Framework 4.6.1 ou anterior, mas estão sendo executados no .NET Framework 4.6.2 ou posterior, podem habilitar as alterações na normalização do caminho adicionando a seguinte linha à seção [ \<de>de tempo de execução](../configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="23174-124">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="23174-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="23174-125">See also</span></span>

- [<span data-ttu-id="23174-126">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="23174-126">Application compatibility</span></span>](application-compatibility.md)
