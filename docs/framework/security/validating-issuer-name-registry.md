---
title: Validando Registro do nome do emissor
ms.date: 03/30/2017
ms.assetid: c4644dd1-dead-48ff-abeb-7bffae69a6ac
ms.openlocfilehash: dc7da9d3dc4ab696d8c27d8e12583b8d06e747fe
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045308"
---
# <a name="validating-issuer-name-registry"></a>Validando Registro do nome do emissor
O VINR (Registro de Validação de Nome do Emissor) para o Windows Identity Foundation permite que aplicativos de vários locatários garantam que um token de entrada seja emitido por um provedor de identidade e locatário confiável. Essa funcionalidade é particularmente útil para aplicativos de vários locatários que usam o Active Directory do Microsoft Azure porque todos os tokens emitidos pelo AD do Microsoft Azure são assinados usando o mesmo certificado. Para diferenciar entre solicitações de vários locatários que usam o mesmo certificado – e, consequentemente, têm a mesma impressão digital – seu aplicativo deve persistir no nome do emissor para que cada locatário execute a lógica de validação. O VINR fornece essa funcionalidade e também permite que você adicione lógica de validação personalizada ou armazene os dados do Registro do emissor em locais diferentes de um arquivo de configuração. A extensão pode ser adicionada ao pipeline WIF do aplicativo ou pode ser usada de modo independente.  
  
 O VINR está disponível como um pacote NuGet. Consulte [Baixando o pacote do Registro do Nome do Emissor de Validação](downloading-the-validating-issuer-name-registry-package.md) para obter mais informações.  
  
## <a name="scenarios"></a>Cenários  
 O VINR permite o seguinte cenário principal:  
  
- **Validar um token em um aplicativo multilocatário**: Nesse cenário, uma empresa chamada Litware desenvolveu um aplicativo multilocatário que usa um provedor de identidade, como o Windows Azure AD. Esse aplicativo atende a dois clientes: Contoso e fabrikam. Quando um usuário da Fabrikam se autentica no aplicativo da Litware, o token resultante do AD do Microsoft Azure é assinado usando seu certificado padrão e a solicitação é emitida pela Fabrikam. O aplicativo precisa verificar se o nome do emissor e o token são válidos, além de diferenciar as solicitações da Contoso que são assinadas usando o mesmo certificado do AD do Microsoft Azure. O VINR torna fácil para o aplicativo da Litware diferenciar e validar solicitações de vários locatários, como Contoso e Fabrikam.  
  
## <a name="features"></a>Recursos  
 O VINR oferece os seguintes recursos:  
  
- **Nome do emissor e validação de token para aplicativos multilocatário**: Valida o token de entrada verificando o nome do emissor (locatário) e se o token foi assinado usando um certificado válido do provedor de identidade.  
  
- **Extensibilidade para lógica de validação personalizada e armazenamentos de dados**: Fornece extensibilidade para injetar sua própria lógica de validação e para especificar um armazenamento de dados que não seja o arquivo de configuração padrão.
