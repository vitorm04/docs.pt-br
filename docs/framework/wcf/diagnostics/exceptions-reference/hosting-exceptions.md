---
title: Exceções de hospedagem
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: f2bc7d0ca09faa2598990437295d1abf0cff3c45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934726"
---
# <a name="hosting-exceptions"></a>Exceções de hospedagem
Este tópico lista todas as exceções geradas pela hospedagem.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|O URI completo não é permitido. URIs completos não são permitidos para a API ServiceHostingEnvironment. Use um caminho virtual para o serviço correspondente.|  
|Hosting_BuildProviderCouldNotCreateType|O tipo CLR especificado não pode ser carregado durante a compilação de serviço. Verifique se esse tipo é definido tanto em um arquivo de código-fonte localizado na caixa de diálogo \\diretório \App_Code, contido em um assembly compilado localizado na caixa de diálogo \\\bin diretório ou presentes em um assembly instalado no Cache de Assembly Global. O nome do tipo diferencia maiusculas de minúsculas. Os diretórios, como \\\App_Code e \\\bin deve estar localizado no diretório raiz do aplicativo. O \\\App_Code e \\\bin diretórios não podem ser aninhados em subdiretórios.|
