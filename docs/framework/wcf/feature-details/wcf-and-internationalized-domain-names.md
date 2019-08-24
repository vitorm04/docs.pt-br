---
title: WCF e nomes de domínio internacionalizados
ms.date: 03/30/2017
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
ms.openlocfilehash: 1db62f3e7d073fd1bf9bf9d4d0e17703310f2e69
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988589"
---
# <a name="wcf-and-internationalized-domain-names"></a><span data-ttu-id="4750b-102">WCF e nomes de domínio internacionalizados</span><span class="sxs-lookup"><span data-stu-id="4750b-102">WCF and Internationalized Domain Names</span></span>
<span data-ttu-id="4750b-103">Foi adicionado suporte para permitir serviços WCF com IDNs (nomes de domínio internacionalizados).</span><span class="sxs-lookup"><span data-stu-id="4750b-103">Support has been added to allow for WCF services with Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="4750b-104">Um nome de domínio internacionalizado é um nome de domínio que contém caracteres não ASCII.</span><span class="sxs-lookup"><span data-stu-id="4750b-104">An internationalized domain name is a domain name that contains non-ASCII characters.</span></span> <span data-ttu-id="4750b-105">Esse suporte inclui a capacidade de hospedar um serviço WCF com um nome IDN e um cliente WCF para se comunicar com um serviço Web com um nome IDN.</span><span class="sxs-lookup"><span data-stu-id="4750b-105">This support includes both the ability to host a WCF service with an IDN name and a WCF client to talk to a web service with an IDN name.</span></span>  
  
## <a name="systemuri-and-idn"></a><span data-ttu-id="4750b-106">System. URI e IDN</span><span class="sxs-lookup"><span data-stu-id="4750b-106">System.Uri and IDN</span></span>  
 <span data-ttu-id="4750b-107"><xref:System.Uri>tem duas propriedades <xref:System.Uri.Host%2A> e <xref:System.Uri.DnsSafeHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="4750b-107"><xref:System.Uri> has two properties <xref:System.Uri.Host%2A> and <xref:System.Uri.DnsSafeHost%2A>.</span></span> <span data-ttu-id="4750b-108">Essas propriedades contêm valores Unicode ou Punycode dependendo das definições de configuração de IDN.</span><span class="sxs-lookup"><span data-stu-id="4750b-108">These properties contain Unicode or Punycode values depending upon the IDN configuration settings.</span></span>  
  
 <span data-ttu-id="4750b-109">O IDN está habilitado no arquivo de configuração de um aplicativo usando o seguinte XML</span><span class="sxs-lookup"><span data-stu-id="4750b-109">IDN is enabled in an application’s configuration file using the following XML</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 <span data-ttu-id="4750b-110">O \<elemento > IDN contém o atributo enabled que pode ser definido como um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="4750b-110">The \<idn> element contains the enabled attribute which can be set to one of the following values:</span></span>  
  
1. <span data-ttu-id="4750b-111">"None"</span><span class="sxs-lookup"><span data-stu-id="4750b-111">"None"</span></span>  
  
2. <span data-ttu-id="4750b-112">"AllExceptIntranet"</span><span class="sxs-lookup"><span data-stu-id="4750b-112">"AllExceptIntranet"</span></span>  
  
3. <span data-ttu-id="4750b-113">Os</span><span class="sxs-lookup"><span data-stu-id="4750b-113">"All"</span></span>  
  
 <span data-ttu-id="4750b-114">Quando a configuração de IDN é definida como "None", nenhuma conversões é executada por URI. host ou URI. DnsSafeHost.</span><span class="sxs-lookup"><span data-stu-id="4750b-114">When the IDN setting is set to "None", no conversions are performed by Uri.Host or Uri.DnsSafeHost.</span></span> <span data-ttu-id="4750b-115">Quando a configuração de IDN é definida como "All", Uri. O host permanece Unicode e URI. DnsSafeHost é convertido em Punycode.</span><span class="sxs-lookup"><span data-stu-id="4750b-115">When the IDN setting is set to "All", uri.Host remains Unicode and uri.DnsSafeHost is converted to Punycode.</span></span> <span data-ttu-id="4750b-116">Quando a configuração de IDN é definida como "AllExceptIntranet", Uri. DnsSafeHost é convertido em Punycode para endereços da Internet e permanece Unicode para endereços de intranet.</span><span class="sxs-lookup"><span data-stu-id="4750b-116">When the IDN setting is set to "AllExceptIntranet", uri.DnsSafeHost is converted to Punycode for internet addresses, and remains Unicode for intranet addresses.</span></span> <span data-ttu-id="4750b-117">Essa configuração é importante para a resolução correta de nomes DNS.</span><span class="sxs-lookup"><span data-stu-id="4750b-117">This setting is important for correct DNS name resolution.</span></span> <span data-ttu-id="4750b-118">Observe que essa configuração não precisa ser configurada para o Windows 8 e versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="4750b-118">Note this setting is not required to be configured for Windows 8 and newer versions.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="4750b-119">Você nunca deve embutir em código um endereço usando Punycode.</span><span class="sxs-lookup"><span data-stu-id="4750b-119">You should never hard-code an address using Punycode.</span></span> <span data-ttu-id="4750b-120">O WCF irá convertê-lo para você com base nas definições de configuração aplicadas.</span><span class="sxs-lookup"><span data-stu-id="4750b-120">WCF will convert it for you based on the configuration settings you apply.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="4750b-121">Ao adicionar caracteres Unicode a applicationHost. exe. config, salve o arquivo usando a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="4750b-121">When adding Unicode characters to applicationHost.exe.config, save the file using the UTF-8 encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4750b-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4750b-122">See also</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
