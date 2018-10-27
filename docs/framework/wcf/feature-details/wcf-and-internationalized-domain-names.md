---
title: WCF e nomes de domínio internacionalizados
ms.date: 03/30/2017
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
ms.openlocfilehash: a0d4a5b4fe5dd3bc7cf41c8c6ad320dd83861aec
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187917"
---
# <a name="wcf-and-internationalized-domain-names"></a><span data-ttu-id="c52c7-102">WCF e nomes de domínio internacionalizados</span><span class="sxs-lookup"><span data-stu-id="c52c7-102">WCF and Internationalized Domain Names</span></span>
<span data-ttu-id="c52c7-103">Foi adicionado suporte para permitir que os serviços WCF com nomes de domínio internacionalizado (IDN).</span><span class="sxs-lookup"><span data-stu-id="c52c7-103">Support has been added to allow for WCF services with Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="c52c7-104">Um nome de domínio internacionalizados é um nome de domínio que contém caracteres não ASCII.</span><span class="sxs-lookup"><span data-stu-id="c52c7-104">An internationalized domain name is a domain name that contains non-ASCII characters.</span></span> <span data-ttu-id="c52c7-105">Esse suporte inclui a capacidade de hospedar um serviço WCF com um nome IDN e um cliente WCF para se comunicar com um serviço web com um nome IDN.</span><span class="sxs-lookup"><span data-stu-id="c52c7-105">This support includes both the ability to host a WCF service with an IDN name and a WCF client to talk to a web service with an IDN name.</span></span>  
  
## <a name="systemuri-and-idn"></a><span data-ttu-id="c52c7-106">System. URI e a IDN</span><span class="sxs-lookup"><span data-stu-id="c52c7-106">System.Uri and IDN</span></span>  
 <span data-ttu-id="c52c7-107"><xref:System.Uri> tem duas propriedades <xref:System.Uri.Host%2A> e <xref:System.Uri.DnsSafeHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="c52c7-107"><xref:System.Uri> has two properties <xref:System.Uri.Host%2A> and <xref:System.Uri.DnsSafeHost%2A>.</span></span> <span data-ttu-id="c52c7-108">Essas propriedades contêm valores Unicode ou Punycode dependendo das configurações de configuração de IDN.</span><span class="sxs-lookup"><span data-stu-id="c52c7-108">These properties contain Unicode or Punycode values depending upon the IDN configuration settings.</span></span>  
  
 <span data-ttu-id="c52c7-109">IDN estar habilitado no arquivo de configuração de um aplicativo usando o seguinte XML</span><span class="sxs-lookup"><span data-stu-id="c52c7-109">IDN is enabled in an application’s configuration file using the following XML</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 <span data-ttu-id="c52c7-110">O \<idn > elemento contém o atributo habilitado, que pode ser definido como um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="c52c7-110">The \<idn> element contains the enabled attribute which can be set to one of the following values:</span></span>  
  
1.  <span data-ttu-id="c52c7-111">"None"</span><span class="sxs-lookup"><span data-stu-id="c52c7-111">"None"</span></span>  
  
2.  <span data-ttu-id="c52c7-112">"AllExceptIntranet"</span><span class="sxs-lookup"><span data-stu-id="c52c7-112">"AllExceptIntranet"</span></span>  
  
3.  <span data-ttu-id="c52c7-113">"Tudo"</span><span class="sxs-lookup"><span data-stu-id="c52c7-113">"All"</span></span>  
  
 <span data-ttu-id="c52c7-114">Quando a configuração de IDN é definida como "None", nenhuma conversão é realizada pelo URI ou DnsSafeHost.</span><span class="sxs-lookup"><span data-stu-id="c52c7-114">When the IDN setting is set to "None", no conversions are performed by Uri.Host or Uri.DnsSafeHost.</span></span> <span data-ttu-id="c52c7-115">Quando a configuração de IDN é definida como "All", do uri. Host permanece Unicode e uri. DnsSafeHost é convertido em Punycode.</span><span class="sxs-lookup"><span data-stu-id="c52c7-115">When the IDN setting is set to "All", uri.Host remains Unicode and uri.DnsSafeHost is converted to Punycode.</span></span> <span data-ttu-id="c52c7-116">Quando a configuração de IDN é definida como "AllExceptIntranet", o uri. DnsSafeHost é convertido em Punycode para endereços da internet e permanece Unicode para endereços da intranet.</span><span class="sxs-lookup"><span data-stu-id="c52c7-116">When the IDN setting is set to "AllExceptIntranet", uri.DnsSafeHost is converted to Punycode for internet addresses, and remains Unicode for intranet addresses.</span></span> <span data-ttu-id="c52c7-117">Essa configuração é importante para a resolução de nome DNS correta.</span><span class="sxs-lookup"><span data-stu-id="c52c7-117">This setting is important for correct DNS name resolution.</span></span> <span data-ttu-id="c52c7-118">Observe que essa configuração não é necessário para ser configurado para o Windows 8 e versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="c52c7-118">Note this setting is not required to be configured for Windows 8 and newer versions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="c52c7-119">Você deve nunca embutir um endereço usando Punycode.</span><span class="sxs-lookup"><span data-stu-id="c52c7-119">You should never hard-code an address using Punycode.</span></span> <span data-ttu-id="c52c7-120">WCF irá convertê-lo para você com base nas definições de configuração que se aplicam.</span><span class="sxs-lookup"><span data-stu-id="c52c7-120">WCF will convert it for you based on the configuration settings you apply.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="c52c7-121">Ao adicionar caracteres Unicode a applicationHost.exe.config, salve o arquivo usando a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c52c7-121">When adding Unicode characters to applicationHost.exe.config, save the file using the UTF-8 encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c52c7-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c52c7-122">See Also</span></span>  
 <xref:System.Uri?displayProperty=nameWithType>
