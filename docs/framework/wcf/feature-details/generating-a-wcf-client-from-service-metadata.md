---
title: Gerando um cliente do WCF de metadados de serviço
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27f8f545-cc44-412a-b104-617e0781b803
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9eedf84d1dccb8bc2540aca7e6bd338b4e58326d
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/23/2018
---
# <a name="generating-a-wcf-client-from-service-metadata"></a>Gerando um cliente do WCF de metadados de serviço
Este tópico descreve como usar as várias opções no Svcutil.exe para gerar os clientes de documentos de metadados.  
  
 Documentos de metadados podem estar em um armazenamento durável ou ser recuperados online. Recuperação online segue o protocolo WS-MetadataExchange ou o protocolo de descoberta do Microsoft (DISCO). Svcutil.exe emite as seguintes solicitações de metadados ao mesmo tempo para recuperar metadados:  
  
-   Solicitação do WS-MetadataExchange (MEX) para o endereço fornecido.  
  
-   Solicitação MEX para o endereço fornecido com `/mex` anexado.  
  
-   Solicitação DISCO (usando o [DiscoveryClientProtocol](http://go.microsoft.com/fwlink/?LinkId=94777) de serviços Web do ASP.NET) para o endereço fornecido.  
  
 Svcutil.exe gera o cliente com base no arquivo WSDL Web Services Description Language () ou diretiva recebido do serviço. O nome de usuário principal (UPN) é gerado pela concatenação do nome de usuário com "@" e, em seguida, adicionar um nome de domínio totalmente qualificado (FQDN). No entanto, para os usuários registrados no Active Directory, esse formato não é válido e o UPN que a ferramenta gera causa uma falha na autenticação Kerberos com a seguinte mensagem de erro: **Falha na tentativa de logon.** Para resolver esse problema, corrija o arquivo de cliente que gerou a ferramenta manualmente.  
  
```  
svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>  
```  
  
## <a name="referencing-and-sharing-types"></a>Referenciando e tipos de compartilhamento  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/Reference:\<caminho do arquivo >**|Os tipos de referência no assembly especificado. Ao gerar clientes, use esta opção para especificar os assemblies que podem conter tipos que representam os metadados que estão sendo importados.<br /><br /> Forma abreviada: `/r`|  
|**/excludeType:\<type>**|Especifica um nome de tipo totalmente qualificado ou qualificado do assembly a ser excluído dos tipos de contrato referenciados.<br /><br /> Forma abreviada: `/et`|  
  
## <a name="choosing-a-serializer"></a>Escolhendo um serializador  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/serializer:Auto**|Seleciona automaticamente o serializador. Isso usa o `DataContract` serializador. Se isso falhar, o `XmlSerializer` é usado.<br /><br /> Forma abreviada: `/ser:Auto`|  
|**/serializer:DataContractSerializer**|Gera os tipos de dados que usam o `DataContract` serializador para serialização e desserialização.<br /><br /> Forma abreviada: `/ser:DataContractSerializer`|  
|**/serializer:XmlSerializer**|Gera os tipos de dados que usam o `XmlSerializer` para serialização e desserialização.<br /><br /> Forma abreviada: `/ser:XmlSerializer`|  
|**/importXmlTypes**|Configura o `DataContract` serializador para importar não`DataContract` tipos como `IXmlSerializable` tipos.<br /><br /> Forma abreviada: `/ixt`|  
|**/dataContractOnly**|Gera código para `DataContract` tipos somente. `ServiceContract` tipos são gerados.<br /><br /> Você deve especificar somente os arquivos de metadados local para essa opção.<br /><br /> Forma abreviada: `/dconly`|  
  
## <a name="choosing-a-language-for-the-client"></a>Escolher um idioma para o cliente  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/language:\<language>**|Especifica a linguagem de programação a ser usada para gerar o código. Forneça um nome de idioma registrado no arquivo Machine. config ou o nome totalmente qualificado de uma classe que herda de <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Valores: c#, cs, csharp, vb, vbs, visualbasic, vbscript, javascript, c + +, mc, cpp<br /><br /> Padrão: csharp<br /><br /> Forma abreviada: `/l`<br /><br /> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Classe CodeDomProvider](http://go.microsoft.com/fwlink/?LinkId=94778).|  
  
## <a name="choosing-a-namespace-for-the-client"></a>Escolhendo um Namespace para o cliente  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/namespace:\<string,string>**|Especifica um mapeamento de um esquema XML ou de WSDL `targetNamespace` para um namespace de tempo de execução (CLR) de linguagem comum. Usando um caractere curinga (*) para o `targetNamespace` mapeia todos os `targetNamespaces` sem um mapeamento explícito esse namespace CLR.<br /><br /> Para certificar-se de que o nome do contrato de mensagem não entrarem em conflito com o nome da operação, qualifique a referência de tipo com dois-pontos duplo (`::`) ou verifique se os nomes são exclusivos.<br /><br /> Padrão: Derivado do namespace de destino do documento do esquema para `DataContracts`. O namespace padrão é usado para todos os outros tipos gerados.<br /><br /> Forma abreviada: `/n`|  
  
## <a name="choosing-a-data-binding"></a>Escolhendo uma associação de dados  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/enableDataBinding**|Implementa o <xref:System.ComponentModel.INotifyPropertyChanged> interface em todos os `DataContract` tipos para habilitar a associação de dados.<br /><br /> Forma abreviada: `/edb`|  
  
## <a name="generating-configuration"></a>Gerar a configuração  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/config:\<configFile>**|Especifica o nome do arquivo para o arquivo de configuração gerada.<br /><br /> Padrão: output.config|  
|**/mergeConfig**|Mescla a configuração gerada em um arquivo existente, em vez de substituir o arquivo existente.|  
|**/noConfig**|Não gera arquivos de configuração.|  
  
## <a name="see-also"></a>Consulte também  
 [Usando metadados](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Visão geral da arquitetura de metadados](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
