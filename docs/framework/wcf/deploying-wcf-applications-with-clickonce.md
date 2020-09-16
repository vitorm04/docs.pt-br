---
title: Implantando aplicativos do WCF com um clique
ms.date: 03/30/2017
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
ms.openlocfilehash: 52657c5f3b5bc6c57c59f4ef23e73089f3c681eb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550365"
---
# <a name="deploying-wcf-applications-with-clickonce"></a><span data-ttu-id="66a62-102">Implantando aplicativos do WCF com um clique</span><span class="sxs-lookup"><span data-stu-id="66a62-102">Deploying WCF Applications with ClickOnce</span></span>
<span data-ttu-id="66a62-103">Aplicativos cliente que usam Windows Communication Foundation (WCF) podem ser implantados usando a tecnologia ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="66a62-103">Client applications using Windows Communication Foundation (WCF) may be deployed using ClickOnce technology.</span></span> <span data-ttu-id="66a62-104">Essa tecnologia permite que eles aproveitem as proteções de segurança de tempo de execução fornecidas pela segurança de acesso ao código, desde que sejam assinadas digitalmente com um certificado confiável.</span><span class="sxs-lookup"><span data-stu-id="66a62-104">This technology allows them to take advantage of the runtime security protections provided by Code Access Security, provided that they are digitally signed with a trusted certificate.</span></span> <span data-ttu-id="66a62-105">O certificado usado para assinar o aplicativo ClickOnce deve residir no repositório de fornecedores confiáveis, e a política de segurança local no computador cliente deve ser configurada para conceder permissões de confiança total a aplicativos assinados com o certificado do Publicador.</span><span class="sxs-lookup"><span data-stu-id="66a62-105">The certificate used to sign the ClickOnce application must reside in the Trusted Publisher store, and the local security policy on the client machine must be configured to grant Full Trust permissions to applications signed with the publisher's certificate.</span></span>  
  
 <span data-ttu-id="66a62-106">Para obter informações sobre como configurar aplicativos ClickOnce e editores confiáveis, consulte [Configurando editores confiáveis do ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="66a62-106">For information on configuring ClickOnce applications and trusted publishers, see [Configuring ClickOnce Trusted Publishers](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a62-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="66a62-107">See also</span></span>

- [<span data-ttu-id="66a62-108">Visão geral da implantação de aplicativos confiáveis</span><span class="sxs-lookup"><span data-stu-id="66a62-108">Trusted Application Deployment Overview</span></span>](/visualstudio/deployment/trusted-application-deployment-overview)
- <span data-ttu-id="66a62-109">[Implantação do ClickOnce para aplicativos Windows Forms](/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="66a62-109">[ClickOnce Deployment for Windows Forms Applications](/previous-versions/visualstudio/visual-studio-2008/wh45kb66(v=vs.90))</span></span>
