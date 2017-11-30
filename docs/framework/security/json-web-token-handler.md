---
title: Manipulador de Token da Web JSON
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 6772d484fa4d0ed3948ecee26adb2cf886340f11
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="json-web-token-handler"></a>Manipulador de Token da Web JSON
A extensão do Manipulador de Tokens da Web JSON para Windows Identity Foundation permite que você crie e valide JWT (Tokens da Web JSON) em seus aplicativos. O Manipulador de Tokens JWT pode ser configurado para ser executado no pipeline WIF como outros manipuladores de tokens de segurança internos, mas também pode ser usado de forma independente para executar a validação do token em aplicativos leves. O Manipulador de Tokens JWT é particularmente útil ao usar um esquema de token portador OAuth 2.0, como a autenticação no Active Directory do Microsoft Azure.  
  
 O Manipulador de Tokens JWT está disponível como um pacote NuGet. Consulte [Baixando o pacote do manipulador de token Web JSON](../../../docs/framework/security/downloading-the-json-web-token-handler-package.md) para obter mais informações.  
  
## <a name="scenarios"></a>Cenários  
 O Manipulador de Tokens JWT permite os seguintes cenários principais:  
  
-   **Validar um token JWT em um aplicativo para servidores**: nesse cenário, uma empresa chamada Litware tem um aplicativo para servidores que usa WIF para manipular solicitações de logon da Web. A Litware deseja permitir que seu aplicativo use tokens JWT para autenticação. O aplicativo é atualizado com o Manipulador de Tokens JWT e depois a configuração do aplicativo é atualizada para adicionar o Manipulador de Tokens JWT no pipeline WIF. Depois que as atualizações são feitas e uma nova solicitação entra no pipeline WIF, o token do JWT é validado usando o novo manipulador, e a autenticação bem-sucedida ocorre.  
  
-   **Validar um token JWT em um serviço Web REST**: nesse cenário, uma empresa chamada Litware tem um serviço Web REST que é protegido pelo Microsoft Azure Active Directory. As solicitações para o serviço Web devem ser autenticadas pelo AD do Microsoft Azure, que emite um token JWT na autenticação bem-sucedida. A Litware tem um aplicativo cliente que precisa acessar o serviço Web. O cliente faz uma solicitação ao serviço Web e apresenta seu token JWT do AD do Microsoft Azure, que é validado pelo serviço Web usando o Manipulador de Tokens JWT. Depois que o Manipulador de Tokens JWT valida o token, o recurso desejado é retornado para o cliente pelo serviço Web.  
  
## <a name="features"></a>Recursos  
 O Manipulador de Tokens JWT oferece os seguintes recursos:  
  
-   **Validar um Token JWT**: os tokens JWT podem ser facilmente validados pela lógica de validação do manipulador de tokens, como uma parte do pipeline WIF do aplicativo ou chamados independentemente do WIF  
  
-   **Criar um Token JWT**: o Manipulador de Tokens JWT pode ser usado para criar tokens JWT para autorização em serviços de downstream
