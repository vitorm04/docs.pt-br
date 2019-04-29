---
title: Implantando um projeto de biblioteca do WCF
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 1ba26a7e68fe262dc5f4f569647af1ebb94e03a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785119"
---
# <a name="deploying-a-wcf-library-project"></a>Implantando um projeto de biblioteca do WCF
Este tópico descreve como você pode implantar um projeto de biblioteca de serviço do Windows Communication Foundation (WCF).  
  
## <a name="deploying-a-wcf-service-library"></a>Implantar uma biblioteca de serviço do WCF  
 Uma biblioteca de serviço do WCF é uma biblioteca de vínculo dinâmico (DLL). Como tal, ele não pode ser executado por conta própria. Ele precisa ser implantado em um ambiente de hospedagem. Para obter mais informações sobre esse processo, consulte [hospedagem e consumindo serviços WCF](https://go.microsoft.com/fwlink/?LinkId=99932).  
  
 Uma biblioteca de serviços WCF pode ser implantada como qualquer outro serviço do WCF. No entanto, lembre-se que [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] não dá suporte a configuração para DLLs. <xref:System.Configuration> dá suporte a um arquivo de configuração por domínio de aplicativo. O projeto de biblioteca de serviço do WCF elimina essa limitação, fornecendo um arquivo App. config para a biblioteca durante o desenvolvimento. No entanto, o arquivo App. config não é reconhecido após a implantação.  
  
 Você precisa mover seu código de configuração para o arquivo de configuração reconhecido pelo seu ambiente de hospedagem. Para auto-hospedagem, você deve copiar o conteúdo do arquivo App. config no arquivo App. config do executável de hospedagem. Se você usar o IIS para hospedar seu serviço, você deve copiar o conteúdo do arquivo App. config no arquivo Web. config do diretório virtual.
