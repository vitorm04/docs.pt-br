---
title: 'Comunicações principais: Suporte de Webhost'
ms.date: 03/30/2017
ms.assetid: 034c501f-96f9-4ef7-9602-3ac21788fd3e
ms.openlocfilehash: 8ee107ffcb9fab629541ce004d1c587fcad652c8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503452"
---
# <a name="core-communications-webhost-support"></a>Comunicações principais: Suporte de Webhost

Este tópico lista todas as exceções geradas pelo suporte de Webhost.

## <a name="exception-list"></a>Lista de exceções

|Código do recurso|Cadeia de caracteres de recurso|
|-------------------|---------------------|
|Hosting_CompatibilityServiceNotHosted|Este serviço requer compatibilidade do ASP.NET. Ele também deve ser hospedado no IIS. A hospedar o serviço no IIS com compatibilidade com ASP.NET ativada no Web. config ou defina a propriedade de AspNetCompatibilityRequirementsAttribute para um valor diferente de necessário.|
|Hosting_ListenerNotFoundForActivationInRecycling|Nenhum canal está escutando ativamente no endereço especificado. Se a reciclagem de um aplicativo, o serviço será fechado.|
|Hosting_NonHTTPInCompatibilityMode|Somente os protocolos que têm suporte de compatibilidade do ASP.NET são HTTP e HTTPS. Remova o ponto de extremidade especificado ou desabilite a compatibilidade do ASP.NET para o aplicativo.|
|Hosting_ProcessNotExecutingUnderHostedContext|O processo de hospedagem especificado não pode ser invocado dentro do ambiente de hospedagem atual. Essa API requer que o aplicativo de chamada hospedado no Internet Information Services ou o serviço de ativação de processos do Windows.|
|Hosting_ServiceCompatibilityRequire|O serviço não pode ser ativado porque ele requer compatibilidade do ASP.NET. Compatibilidade do ASP.NET não está habilitada para este aplicativo. Habilitar a compatibilidade do ASP.NET no arquivo Web. config ou defina o AspNetCompatibilityRequirementsAttribute.AspNetCompatibility.|
