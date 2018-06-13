---
title: Implantando um projeto de biblioteca do WCF
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: fb400a4d1ebba691222ad7fc9d2c09f1051591da
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803017"
---
# <a name="deploying-a-wcf-library-project"></a>Implantando um projeto de biblioteca do WCF
Este tópico descreve como você pode implantar um projeto de biblioteca de serviço do Windows Communication Foundation (WCF).  
  
## <a name="deploying-a-wcf-service-library"></a>Implantando uma biblioteca de serviços WCF  
 Uma biblioteca de serviços do WCF é uma biblioteca de vínculo dinâmico (DLL). Como tal, ele não pode ser executado por conta própria. Ele precisa ser implantado em um ambiente de hospedagem. Para obter mais informações sobre esse processo, consulte [hospedagem e consumindo serviços WCF](http://go.microsoft.com/fwlink/?LinkId=99932).  
  
 Uma biblioteca de serviços WCF pode ser implantada como qualquer outro serviço do WCF. No entanto, lembre-se que [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] não oferece suporte à configuração para DLLs. <xref:System.Configuration> oferece suporte a um arquivo de configuração por domínio de aplicativo. O projeto de biblioteca de serviço WCF elimina essa limitação, fornecendo um arquivo App. config para a biblioteca durante o desenvolvimento. No entanto, o arquivo App. config não é reconhecido após a implantação.  
  
 Você precisa mover seu código de configuração para o arquivo de configuração reconhecido pelo seu ambiente de hospedagem. Para auto-hospedagem, você deve copiar o conteúdo do arquivo App. config no arquivo App. config do executável de hospedagem. Se você usar o IIS para hospedar seu serviço, você deve copiar o conteúdo do arquivo App. config no arquivo Web. config do diretório virtual.
