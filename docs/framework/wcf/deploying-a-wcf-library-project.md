---
title: Implantando um projeto de biblioteca do WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 04567b0b06ef5c8f105e866e150bfaa221d64057
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="deploying-a-wcf-library-project"></a>Implantando um projeto de biblioteca do WCF
Este tópico descreve como você pode implantar um [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] projeto de biblioteca de serviço.  
  
## <a name="deploying-a-wcf-service-library"></a>Implantando uma biblioteca de serviços WCF  
 Um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] biblioteca de serviço é uma biblioteca de vínculo dinâmico (DLL). Como tal, ele não pode ser executado por conta própria. Ele precisa ser implantado em um ambiente de hospedagem. Para obter mais informações sobre esse processo, consulte [hospedagem e consumindo serviços WCF](http://go.microsoft.com/fwlink/?LinkId=99932).  
  
 Um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] biblioteca de serviço pode ser implantada como qualquer outro [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço. No entanto, lembre-se que [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] não oferece suporte à configuração para DLLs. <xref:System.Configuration>oferece suporte a um arquivo de configuração por domínio de aplicativo. O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projeto de biblioteca de serviço elimina essa limitação, fornecendo um arquivo App. config para a biblioteca durante o desenvolvimento. No entanto, o arquivo App. config não é reconhecido após a implantação.  
  
 Você precisa mover seu código de configuração para o arquivo de configuração reconhecido pelo seu ambiente de hospedagem. Para auto-hospedagem, você deve copiar o conteúdo do arquivo App. config no arquivo App. config do executável de hospedagem. Se você usar o IIS para hospedar seu serviço, você deve copiar o conteúdo do arquivo App. config no arquivo Web. config do diretório virtual.
