---
title: Exceções de hospedagem
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: f2bc7d0ca09faa2598990437295d1abf0cff3c45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33469431"
---
# <a name="hosting-exceptions"></a>Exceções de hospedagem
Este tópico lista todas as exceções geradas pelo hospedagem.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|O URI completo não é permitido. URIs completos não são permitidos para a API ServiceHostingEnvironment. Use um caminho virtual para o serviço correspondente.|  
|Hosting_BuildProviderCouldNotCreateType|Não é possível carregar o tipo CLR especificado durante a compilação do serviço. Verifique se esse tipo ou é definido em um arquivo de origem localizado no aplicativo de \\diretório \App_Code, contido em um assembly compilado localizado no aplicativo de \\\bin diretório ou presente em um assembly instalado no Cache de Assembly Global. O nome do tipo diferencia maiusculas de minúsculas. Os diretórios, como \\\App_Code e \\\bin deve estar localizado no diretório raiz do aplicativo. O \\\App_Code e \\\bin diretórios não podem ser aninhados em subdiretórios.|
