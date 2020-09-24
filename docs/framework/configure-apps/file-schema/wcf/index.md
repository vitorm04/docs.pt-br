---
title: Esquema de configuração do WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: ab64b41e6e79c934ac0145dd7eec0a943f5dc473
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165124"
---
# <a name="wcf-configuration-schema"></a>Esquema de configuração do WCF

Os elementos de configuração do Windows Communication Foundation (WCF) permitem configurar aplicativos cliente e serviço WCF. Você pode usar a [Ferramenta Editor de Configuração (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) para criar e modificar arquivos de configuração para clientes e serviços. Como os arquivos de configuração são formatados como XML, você deverá estar familiarizado com XML se desejar editá-los manualmente usando um editor de texto. Caso contrário, você pode ter problemas, como uma marca de elemento XML unfound ou atributo. Isso ocorre porque marcas de elementos XML e atributos diferenciam maiúsculas de minúsculas.  
  
 O sistema de configuração do WCF é baseado no <xref:System.Configuration> namespace. Portanto, você pode usar todos os recursos padrão fornecidos pelo namespace <xref:System.Configuration>, como bloqueio de configuração, criptografia e mesclagem para aumentar a segurança de seu aplicativo e de sua configuração. Para obter mais informações sobre esses conceitos, consulte os tópicos a seguir.  
  
 [Criptografando informações de configuração](/previous-versions/aspnet/53tyfkaw(v=vs.100))  
  
 [Locking Configuration Settings](/previous-versions/aspnet/55th21y4(v=vs.100)) (Bloqueando as definições de configuração)  
  
 Esta seção descreve todos os possíveis valores de cada item de configuração e como eles interagem com outros elementos de configuração do WCF. O mapa a seguir ilustra o esquema de configuração do WCF:  
  
 ![Diagrama que mostra o esquema de configuração do WCF.](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
> Você deve proteger as seções de configuração do WCF em seus arquivos de configuração de aplicativo (app.config) com ACLs (listas de controle de acesso) apropriadas para evitar possíveis ameaças à segurança.  Por exemplo, você deve garantir que somente pessoas apropriadas possam acessar ou modificar as configurações de segurança em associações de aplicativo ou a seção do modelo de serviço no arquivo de configuração de um serviço.  
  
## <a name="in-this-section"></a>Nesta seção  

 [\<system.serviceModel>](system-servicemodel.md)  
 Descreve o `ServiceModel` elemento.  
  
 [\<system.serviceModel.activation>](system-servicemodel-activation.md)  
 Configura a ferramenta SMSvcHost.exe.  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
 O elemento de nível superior para definir opções ao usar serializadores como o <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="related-sections"></a>Seções relacionadas  

 [Configuring Windows Communication Foundation Applications](../../../wcf/configuring-services.md) (Configurando aplicativos do Windows Communication Foundation)  
 Descreve como configurar clientes e serviços WCF.
