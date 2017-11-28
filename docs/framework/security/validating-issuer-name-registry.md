---
title: Validando Registro do nome do emissor
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4644dd1-dead-48ff-abeb-7bffae69a6ac
caps.latest.revision: "4"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: c6c1b72048f1f7cb421e5a19d34c2c2dea5463ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="validating-issuer-name-registry"></a>Validando Registro do nome do emissor
O VINR (Registro de Validação de Nome do Emissor) para o Windows Identity Foundation permite que aplicativos de vários locatários garantam que um token de entrada seja emitido por um provedor de identidade e locatário confiável. Essa funcionalidade é particularmente útil para aplicativos de vários locatários que usam o Active Directory do Microsoft Azure porque todos os tokens emitidos pelo AD do Microsoft Azure são assinados usando o mesmo certificado. Para diferenciar entre solicitações de vários locatários que usam o mesmo certificado – e, consequentemente, têm a mesma impressão digital – seu aplicativo deve persistir no nome do emissor para que cada locatário execute a lógica de validação. O VINR fornece essa funcionalidade e também permite que você adicione lógica de validação personalizada ou armazene os dados do Registro do emissor em locais diferentes de um arquivo de configuração. A extensão pode ser adicionada ao pipeline WIF do aplicativo ou pode ser usada de modo independente.  
  
 O VINR está disponível como um pacote NuGet. Consulte [Baixando o pacote do Registro do Nome do Emissor de Validação](../../../docs/framework/security/downloading-the-validating-issuer-name-registry-package.md) para obter mais informações.  
  
## <a name="scenarios"></a>Cenários  
 O VINR permite o seguinte cenário principal:  
  
-   **Validar um token em um aplicativo multilocatário**: nesse cenário, uma empresa chamada Litware desenvolveu um aplicativo multilocatário que usa um provedor de identidade como o Microsoft Azure AD. Esse aplicativo atende dois clientes: Contoso e Fabrikam. Quando um usuário da Fabrikam se autentica no aplicativo da Litware, o token resultante do AD do Microsoft Azure é assinado usando seu certificado padrão e a solicitação é emitida pela Fabrikam. O aplicativo precisa verificar se o nome do emissor e o token são válidos, além de diferenciar as solicitações da Contoso que são assinadas usando o mesmo certificado do AD do Microsoft Azure. O VINR torna fácil para o aplicativo da Litware diferenciar e validar solicitações de vários locatários, como Contoso e Fabrikam.  
  
## <a name="features"></a>Recursos  
 O VINR oferece os seguintes recursos:  
  
-   **Validação do nome do emissor e do token para aplicativos multilocatários**: valida o token de entrada verificando o nome do emissor (locatário) e se o token foi assinado usando um certificado válido do provedor de identidade.  
  
-   **Extensibilidade da lógica de validação personalizada e dos armazenamentos de dados**: oferece extensibilidade para injeção de sua própria lógica de validação e especificação de um armazenamento de dados diferente do arquivo de configuração padrão.
