---
title: "WCF e nomes de domínio internacionalizados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ab9346e7826fcef5151ef976b6ca7f25120fa5a3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-and-internationalized-domain-names"></a><span data-ttu-id="0963a-102">WCF e nomes de domínio internacionalizados</span><span class="sxs-lookup"><span data-stu-id="0963a-102">WCF and Internationalized Domain Names</span></span>
<span data-ttu-id="0963a-103">Foi adicionado suporte para permitir que os serviços WCF com nomes de domínio internacionalizados (IDNS).</span><span class="sxs-lookup"><span data-stu-id="0963a-103">Support has been added to allow for WCF services with Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="0963a-104">Um nome de domínio internacionalizados é um nome de domínio que contém caracteres não-ASCII.</span><span class="sxs-lookup"><span data-stu-id="0963a-104">An internationalized domain name is a domain name that contains non-ASCII characters.</span></span> <span data-ttu-id="0963a-105">Esse suporte inclui a capacidade de hospedar um serviço WCF com um nome IDN e um cliente WCF para se comunicar com um serviço web com um nome IDN.</span><span class="sxs-lookup"><span data-stu-id="0963a-105">This support includes both the ability to host a WCF service with an IDN name and a WCF client to talk to a web service with an IDN name.</span></span>  
  
## <a name="systemuri-and-idn"></a><span data-ttu-id="0963a-106">System. URI e IDN</span><span class="sxs-lookup"><span data-stu-id="0963a-106">System.Uri and IDN</span></span>  
 <span data-ttu-id="0963a-107"><xref:System.Uri>tem duas propriedades <xref:System.Uri.Host%2A> e <xref:System.Uri.DnsSafeHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="0963a-107"><xref:System.Uri> has two properties <xref:System.Uri.Host%2A> and <xref:System.Uri.DnsSafeHost%2A>.</span></span> <span data-ttu-id="0963a-108">Essas propriedades contêm valores Unicode ou Punycode, dependendo das configurações de configuração de IDN.</span><span class="sxs-lookup"><span data-stu-id="0963a-108">These properties contain Unicode or Punycode values depending upon the IDN configuration settings.</span></span>  
  
 <span data-ttu-id="0963a-109">IDN está habilitada no arquivo de configuração de um aplicativo usando o seguinte XML</span><span class="sxs-lookup"><span data-stu-id="0963a-109">IDN is enabled in an application’s configuration file using the following XML</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 <span data-ttu-id="0963a-110">O \<idn > elemento contém o atributo enabled que pode ser definido como um dos valores a seguir:</span><span class="sxs-lookup"><span data-stu-id="0963a-110">The \<idn> element contains the enabled attribute which can be set to one of the following values:</span></span>  
  
1.  <span data-ttu-id="0963a-111">"None"</span><span class="sxs-lookup"><span data-stu-id="0963a-111">"None"</span></span>  
  
2.  <span data-ttu-id="0963a-112">"AllExceptIntranet"</span><span class="sxs-lookup"><span data-stu-id="0963a-112">"AllExceptIntranet"</span></span>  
  
3.  <span data-ttu-id="0963a-113">"Todos"</span><span class="sxs-lookup"><span data-stu-id="0963a-113">"All"</span></span>  
  
 <span data-ttu-id="0963a-114">Quando a configuração de IDN é definida como "None", nenhuma conversão é executada pelo URI ou DnsSafeHost.</span><span class="sxs-lookup"><span data-stu-id="0963a-114">When the IDN setting is set to "None", no conversions are performed by Uri.Host or Uri.DnsSafeHost.</span></span> <span data-ttu-id="0963a-115">Quando a configuração de IDN é definida como uri "Todos". Host permanece Unicode e uri. DnsSafeHost é convertido em Punycode.</span><span class="sxs-lookup"><span data-stu-id="0963a-115">When the IDN setting is set to "All", uri.Host remains Unicode and uri.DnsSafeHost is converted to Punycode.</span></span> <span data-ttu-id="0963a-116">Quando a configuração de IDN é definida como "AllExceptIntranet", o uri. DnsSafeHost é convertido em Punycode para endereços da internet e permanece Unicode para endereços da intranet.</span><span class="sxs-lookup"><span data-stu-id="0963a-116">When the IDN setting is set to "AllExceptIntranet", uri.DnsSafeHost is converted to Punycode for internet addresses, and remains Unicode for intranet addresses.</span></span> <span data-ttu-id="0963a-117">Essa configuração é importante para a resolução de nome DNS correta.</span><span class="sxs-lookup"><span data-stu-id="0963a-117">This setting is important for correct DNS name resolution.</span></span> <span data-ttu-id="0963a-118">Observe que essa configuração não deve ser configurado para Windows 8 e versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="0963a-118">Note this setting is not required to be configured for Windows 8 and newer versions.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="0963a-119">Deve nunca codificar um endereço usando Punycode.</span><span class="sxs-lookup"><span data-stu-id="0963a-119">You should never hard-code an address using Punycode.</span></span> <span data-ttu-id="0963a-120">WCF converterá para você com base nas definições de configuração que você aplicar.</span><span class="sxs-lookup"><span data-stu-id="0963a-120">WCF will convert it for you based on the configuration settings you apply.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="0963a-121">Ao adicionar caracteres Unicode para applicationHost.exe.config, salve o arquivo usando a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="0963a-121">When adding Unicode characters to applicationHost.exe.config, save the file using the UTF-8 encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0963a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0963a-122">See Also</span></span>  
 [<span data-ttu-id="0963a-123">System. URI</span><span class="sxs-lookup"><span data-stu-id="0963a-123">System.Uri</span></span>](http://msdn.microsoft.com/library/system.uri.aspx)
