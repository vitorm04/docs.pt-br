---
title: Gerando um cliente do WCF de metadados de serviço
ms.date: 03/30/2017
ms.assetid: 27f8f545-cc44-412a-b104-617e0781b803
ms.openlocfilehash: e40a908894ca5acac33401ff20a9110d617547ec
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963898"
---
# <a name="generating-a-wcf-client-from-service-metadata"></a>Gerando um cliente do WCF de metadados de serviço
Este tópico descreve como usar os vários comutadores em svcutil. exe para gerar clientes de documentos de metadados.  
  
 Os documentos de metadados podem estar em um armazenamento durável ou ser recuperados online. A recuperação online segue o protocolo WS-MetadataExchange ou o protocolo de descoberta da Microsoft (DISCO). Svcutil. exe emite as seguintes solicitações de metadados simultaneamente para recuperar metadados:  
  
- Solicitação WS-MetadataExchange (MEX) para o endereço fornecido.  
  
- Solicitação de MEX para o endereço fornecido com `/mex` acrescentado.  
  
- Solicitação de DISCO (usando o <xref:System.Web.Services.Discovery.DiscoveryClientProtocol> de serviços Web do ASP.NET) para o endereço fornecido.  
  
 Svcutil. exe gera o cliente com base no WSDL (Web Services Description Language) ou no arquivo de política recebido do serviço. O nome UPN é gerado pela concatenação do nome de usuário com "\@" e, em seguida, pela adição de um FQDN (nome de domínio totalmente qualificado). No entanto, para usuários que se registraram em Active Directory, esse formato não é válido e o UPN gerado pela ferramenta causa uma falha na autenticação Kerberos com a seguinte mensagem de erro: **falha na tentativa de logon.** Para resolver esse problema, corrija manualmente o arquivo do cliente gerado pela ferramenta.  
  
```console
svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>  
```  
  
## <a name="referencing-and-sharing-types"></a>Referenciando e compartilhando tipos  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/Reference: caminho do arquivo de\<**|Os tipos de referência no assembly especificado. Ao gerar clientes, use esta opção para especificar os assemblies que podem conter tipos que representam os metadados que estão sendo importados.<br /><br /> Forma abreviada: `/r`|  
|**/excludeType:\<type>**|Especifica um nome de tipo totalmente qualificado ou qualificado do assembly a ser excluído dos tipos de contrato referenciados.<br /><br /> Forma abreviada: `/et`|  
  
## <a name="choosing-a-serializer"></a>Escolhendo um serializador  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/serializer:Auto**|Seleciona automaticamente o serializador. Isso usa o serializador `DataContract`. Se isso falhar, o `XmlSerializer` será usado.<br /><br /> Forma abreviada: `/ser:Auto`|  
|**/serializer:DataContractSerializer**|Gera tipos de dados que usam o serializador `DataContract` para serialização e desserialização.<br /><br /> Forma abreviada: `/ser:DataContractSerializer`|  
|**/serializer:XmlSerializer**|Gera os tipos de dados que usam o `XmlSerializer` para serialização e desserialização.<br /><br /> Forma abreviada: `/ser:XmlSerializer`|  
|**/importXmlTypes**|Configura o serializador de `DataContract` para importar tipos não`DataContract` como `IXmlSerializable` tipos.<br /><br /> Forma abreviada: `/ixt`|  
|**/dataContractOnly**|Gera código somente para tipos de `DataContract`. tipos de `ServiceContract` são gerados.<br /><br /> Você deve especificar somente arquivos de metadados locais para essa opção.<br /><br /> Forma abreviada: `/dconly`|  
  
## <a name="choosing-a-language-for-the-client"></a>Escolhendo um idioma para o cliente  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/Language: > de\<do idioma**|Especifica a linguagem de programação a ser usada para gerar o código. Forneça um nome de idioma registrado no arquivo Machine. config ou o nome totalmente qualificado de uma classe que herda de <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Values: c#, cs, csharp, vb, vbs, visualbasic, vbscript, javascript, c++, mc, cpp<br /><br /> Padrão: csharp<br /><br /> Forma abreviada: `/l`<br /><br /> Para saber mais, confira a classe <xref:System.CodeDom.Compiler.CodeDomProvider>.|  
  
## <a name="choosing-a-namespace-for-the-client"></a>Escolhendo um namespace para o cliente  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/namespace:\<string,string>**|Especifica um mapeamento de um esquema WSDL ou XML `targetNamespace` a um namespace Common Language Runtime (CLR). Usar um caractere curinga (*) para o `targetNamespace` mapeia todos os `targetNamespaces` sem um mapeamento explícito para esse namespace CLR.<br /><br /> Para garantir que o nome do contrato de mensagem não colide com o nome da operação, qualifique a referência de tipo com dois-pontos duplos (`::`) ou verifique se os nomes são exclusivos.<br /><br /> Padrão: derivado do namespace de destino do documento de esquema para `DataContracts`. O namespace padrão é usado para todos os outros tipos gerados.<br /><br /> Forma abreviada: `/n`|  
  
## <a name="choosing-a-data-binding"></a>Escolhendo uma associação de dados  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/enableDataBinding**|Implementa a interface <xref:System.ComponentModel.INotifyPropertyChanged> em todos os tipos de `DataContract` para habilitar a vinculação de dados.<br /><br /> Forma abreviada: `/edb`|  
  
## <a name="generating-configuration"></a>Gerando configuração  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/config:\<configFile>**|Especifica o nome do arquivo de configuração gerado.<br /><br /> Padrão: output.config|  
|**/mergeConfig**|Mescla a configuração gerada em um arquivo existente, em vez de substituir o arquivo existente.|  
|**/noConfig**|Não gera arquivos de configuração.|  
  
## <a name="see-also"></a>Veja também

- [Usando metadados](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Visão geral da arquitetura de metadados](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
