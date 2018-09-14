---
title: Implantando aplicativos do WCF com um clique
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: d733c6f523393737418c6394707c1d4e6e9c1710
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45590488"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="e8ae3-102">Implantando aplicativos do WCF com um clique</span><span class="sxs-lookup"><span data-stu-id="e8ae3-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="e8ae3-103">Aplicativos cliente que usam o Windows Communication Foundation (WCF) podem ser implantados usando a tecnologia ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="e8ae3-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="e8ae3-104">Essa tecnologia permite que eles podem se beneficiar do tempo de execução proteções de segurança fornecidas pela segurança de acesso do código, desde que eles são assinados digitalmente com um certificado confiável.</span><span class="sxs-lookup"><span data-stu-id="e8ae3-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="e8ae3-105">O certificado usado para assinar o aplicativo ClickOnce deve residir no repositório fornecedores confiáveis, e a política de segurança local no computador cliente deve ser configurada para conceder permissões de confiança total para os aplicativos assinados com o certificado do Editor.</span><span class="sxs-lookup"><span data-stu-id="e8ae3-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="e8ae3-106">Para obter informações sobre como configurar aplicativos ClickOnce e editores confiáveis, consulte [Configurar editores confiáveis do ClickOnce](https://go.microsoft.com/fwlink/?LinkId=94774).</span><span class="sxs-lookup"><span data-stu-id="e8ae3-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](https://go.microsoft.com/fwlink/?LinkId=94774).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ae3-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8ae3-107">See Also</span></span>  
 [<span data-ttu-id="e8ae3-108">Visão geral da implantação de aplicativos confiáveis</span><span class="sxs-lookup"><span data-stu-id="e8ae3-108">Trusted Application Deployment Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=94775)  
 [<span data-ttu-id="e8ae3-109">Aplicativos de implantação do ClickOnce para Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e8ae3-109">ClickOnce Deployment for Windows Forms Applications</span></span>](https://go.microsoft.com/fwlink/?LinkId=94776)
