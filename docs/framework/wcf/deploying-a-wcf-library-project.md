---
title: Implantando um projeto de biblioteca do WCF
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 186ce5ae3087fd9b4c7e5c32e110de4bc7d5e578
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801989"
---
# <a name="deploying-a-wcf-library-project"></a>Implantando um projeto de biblioteca do WCF
Este tópico descreve como você pode implantar um projeto de biblioteca de serviços do Windows Communication Foundation (WCF).  
  
## <a name="deploying-a-wcf-service-library"></a>Implantando uma biblioteca de serviços WCF  
 Uma biblioteca de serviços WCF é uma DLL (biblioteca de vínculo dinâmico). Como tal, ele não pode ser executado por conta própria. Ele precisa ser implantado em um ambiente de hospedagem. Para obter mais informações sobre esse processo, consulte [hospedando e consumindo serviços WCF](https://docs.microsoft.com/previous-versions/dotnet/articles/bb332338(v=msdn.10)).  
  
 Uma biblioteca de serviços WCF pode ser implantada como qualquer outro serviço WCF. No entanto, esteja ciente de que .NET Framework não oferece suporte à configuração para DLLs. o <xref:System.Configuration> dá suporte a um arquivo de configuração por domínio de aplicativo. O projeto da biblioteca de serviços WCF alivia essa limitação fornecendo um arquivo app. config para a biblioteca durante o desenvolvimento. No entanto, o arquivo app. config não é reconhecido após a implantação.  
  
 Você precisa mover o código de configuração para o arquivo de configuração reconhecido pelo seu ambiente de hospedagem. Para hospedagem interna, você deve copiar o conteúdo do arquivo app. config no arquivo app. config do executável de hospedagem. Se você usar o IIS para hospedar seu serviço, deverá copiar o conteúdo do arquivo app. config no arquivo Web. config do diretório virtual.
