---
title: Ferramenta geradora de serializador de XML (Sgen.exe)
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: e0fee890f86f4e377a9372d7e4c47ef78effc9fa
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44214895"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>Ferramenta geradora de serializador de XML (Sgen.exe)
O Gerador de Serializador de XML cria um assembly de serialização de XML para tipos em um assembly especificado para aprimorar o desempenho de inicialização de um <xref:System.Xml.Serialization.XmlSerializer> quando ele serializa ou desserializa objetos dos tipos especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
sgen [options]  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/a**[**ssembly**]**:***filename*|Gera o código de serialização para todos os tipos contidos no assembly ou no executável especificado pelo *filename*. Somente um nome de arquivo pode ser fornecido. Se esse argumento for repetido, o último nome de arquivo será usado.|  
|**/c[ompiler]:** *options*|Especifica as opções para passar para o compilador C#. Todas as opções csc.exe têm suporte quando são passadas para o compilador. Isso pode ser usado para especificar que o assembly deve ser assinado e para especificar o arquivo de chave.|  
|**/d**[**ebug**]|Gera uma imagem que pode ser usada com um depurador.|  
|**/f[orce]**|Força a substituição de um assembly existente de mesmo nome. O padrão é **false**.|  
|**/help ou /?**|Exibe sintaxe de comando e opções para a ferramenta.|  
|**/k**[**eep**]|Suprime a exclusão dos arquivos de origem gerados e outros arquivos temporários depois que tiverem sido compilados no assembly de serialização. Isso pode ser usado para determinar se a ferramenta está gerando o código de serialização para um tipo específico.|  
|**/n**[**ologo**]|Suprime a exibição do banner de inicialização da Microsoft.|  
|**/o**[**ut**] **: * * * caminho*|Especifica o diretório no qual salvar o assembly gerado. **Observação:** o nome do assembly gerado é composto pelo nome do assembly de entrada mais “xmlSerializers.dll”.|  
|**/p**[**roxytypes**]|Gera o código de serialização somente para os tipos de proxy de serviço Web XML.|  
|**/r**[**eference**] **: * * * assemblyfiles*|Especifica os assemblies que são referenciados pelos tipos que exigem a serialização de XML. Aceita vários arquivos de assembly separados por vírgulas.|  
|**/s**[**ilent**]|Suprime a exibição de mensagens de sucesso.|  
|**/t**[**IPO**] **: * * * tipo*|Gera o código de serialização somente para o tipo especificado.|  
|**/v**[**erbose**]|Exibe a saída detalhada para depuração. Lista os tipos do assembly de destino que não podem ser serializados com o <xref:System.Xml.Serialization.XmlSerializer>.|  
|**/?**|Exibe sintaxe de comando e opções para a ferramenta.|  
  
## <a name="remarks"></a>Comentários  
 Quando o Gerador do Serializador do XML não é usado, um <xref:System.Xml.Serialization.XmlSerializer> gera o código de serialização e um assembly de serialização para cada tipo toda vez que um aplicativo é executado. Para melhorar o desempenho de inicialização da serialização XML, use a ferramenta Sgen.exe para gerar com antecedência esses assemblies. Esses assemblies podem então ser implantados com o aplicativo.  
  
 O Gerador do Serializador do XML também pode aprimorar o desempenho de clientes que usam proxies de serviço Web XML para se comunicarem com servidores porque o processo de serialização não incorrerá em um acerto de desempenho quando o tipo for carregado pela primeira vez.  
  
 Esses assemblies gerados não podem ser usados no lado do servidor de um serviço Web. Essa ferramenta é somente para clientes de serviço Web e cenários de serialização manual.  
  
 Se o assembly que contém o tipo para serializar é denominado MyType.dll, o assembly de serialização associada será denominado MyType.XmlSerializers.dll.  
  
## <a name="examples"></a>Exemplos  
 O comando a seguir cria um assembly denominado Data.XmlSerializers.dll para serializar todos os tipos contidos no assembly denominado Data.dll.  
  
```  
sgen Data.dll   
```  
  
 O assembly Data.XmlSerializers.dll pode ser referenciado do código que precisa serializar e desserializar os tipos no Data.dll.  
  
## <a name="see-also"></a>Consulte também

- [Ferramentas](../../../docs/framework/tools/index.md)  
- [Visão geral do XML Web Services](https://msdn.microsoft.com/library/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d)  
- [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
