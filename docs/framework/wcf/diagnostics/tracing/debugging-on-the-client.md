---
title: Depuração do cliente
ms.date: 03/30/2017
ms.assetid: 56f9ad05-ea1b-4ef6-85f2-890f7ed71567
ms.openlocfilehash: 0330e0954969fbaf798fe3be029b443f0fa219cd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589351"
---
# <a name="debugging-on-the-client"></a><span data-ttu-id="1d2d0-102">Depuração do cliente</span><span class="sxs-lookup"><span data-stu-id="1d2d0-102">Debugging on the Client</span></span>
<span data-ttu-id="1d2d0-103">Para tornar mais fácil para os usuários escreverem aplicativos cliente para seu serviço WCF, você pode adicionar o [\<serviceDebug>](../../../configure-apps/file-schema/wcf/servicedebug.md) comportamento do serviço ao arquivo de configuração do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="1d2d0-103">To make it easier for users to write client applications for your WCF service, you can add the [\<serviceDebug>](../../../configure-apps/file-schema/wcf/servicedebug.md) service behavior to the configuration file of your service.</span></span> <span data-ttu-id="1d2d0-104">Esse comportamento pode ser usado para publicar páginas de ajuda e retornar informações de exceção gerenciada nos detalhes de falhas de SOAP retornadas ao cliente.</span><span class="sxs-lookup"><span data-stu-id="1d2d0-104">This behavior can be used to publish help pages, and return managed exception information in the details of SOAP faults returned to the client.</span></span>
