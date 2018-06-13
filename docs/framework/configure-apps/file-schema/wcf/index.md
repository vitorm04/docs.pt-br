---
title: Esquema de configuração do WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: bcbc12d35dae59fcd43d5fbf2d4c936c8e4a4423
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357022"
---
# <a name="wcf-configuration-schema"></a>Esquema de configuração do WCF
Elementos de configuração do Windows Communication Foundation (WCF) permitem que você configure aplicativos de cliente e de serviço do WCF. Você pode usar a [Ferramenta Editor de Configuração (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) para criar e modificar arquivos de configuração para clientes e serviços. Como os arquivos de configuração são formatados como XML, você deverá estar familiarizado com XML se desejar editá-los manualmente usando um editor de texto. Caso contrário, você pode ter problemas, como uma marca de elemento XML unfound ou atributo. Isso ocorre porque marcas de elementos XML e atributos diferenciam maiúsculas de minúsculas.  
  
 O sistema de configuração do WCF se baseia o <xref:System.Configuration> namespace. Portanto, você pode usar todos os recursos padrão fornecidos pelo namespace <xref:System.Configuration>, como bloqueio de configuração, criptografia e mesclagem para aumentar a segurança de seu aplicativo e de sua configuração. Para obter mais informações sobre esses conceitos, consulte os tópicos a seguir.  
  
 [Criptografando informações de configuração](http://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [Locking Configuration Settings](http://go.microsoft.com/fwlink/?LinkId=95338) (Bloqueando as definições de configuração)  
  
 Esta seção descreve todos os possíveis valores de cada item de configuração e como eles interagem com outros elementos de configuração do WCF. O mapa a seguir ilustra o esquema de configuração do WCF.  
  
 ![Esquema de configuração do WCF](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")  
  
> [!CAUTION]
>  Você deve proteger seções de configuração do WCF em seus arquivos de configuração de aplicativo (App. config) com apropriado controle listas acesso (ACL) para evitar potenciais ameaças de segurança.  Por exemplo, você deve garantir que somente pessoas apropriadas possam acessar ou modificar as configurações de segurança em associações de aplicativo ou a seção do modelo de serviço no arquivo de configuração de um serviço.  
  
## <a name="in-this-section"></a>Nesta seção  
 [\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 Descreve o `ServiceModel` elemento.  
  
 [\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 Configura a ferramenta SMSvcHost.exe.  
  
 [\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 O elemento de nível superior para definir opções ao usar serializadores como o <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a) (Configurando aplicativos do Windows Communication Foundation)  
 Descreve como configurar clientes e serviços WCF.
