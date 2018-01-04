---
title: "Exceções de hospedagem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b296578efb6eb9b1e6372dbad647fdea22dbaddf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-exceptions"></a>Exceções de hospedagem
Este tópico lista todas as exceções geradas pelo hospedagem.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|O URI completo não é permitido. URIs completos não são permitidos para a API ServiceHostingEnvironment. Use um caminho virtual para o serviço correspondente.|  
|Hosting_BuildProviderCouldNotCreateType|Não é possível carregar o tipo CLR especificado durante a compilação do serviço. Verifique se esse tipo ou é definido em um arquivo de origem localizado no aplicativo de \\diretório \App_Code, contido em um assembly compilado localizado no aplicativo de \\\bin diretório ou presente em um assembly instalado no Cache de Assembly Global. O nome do tipo diferencia maiusculas de minúsculas. Os diretórios, como \\\App_Code e \\\bin deve estar localizado no diretório raiz do aplicativo. O \\\App_Code e \\\bin diretórios não podem ser aninhados em subdiretórios.|
