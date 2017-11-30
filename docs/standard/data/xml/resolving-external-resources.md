---
title: Resolvendo recursos externos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad3fa320-4b8f-4e5c-b549-01157591007a
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 824a35ee5d4ecafc45167ff3f4bc89802af4ed96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="resolving-external-resources"></a>Resolvendo recursos externos
O **XmlResolver** propriedade o **XmlDocument** é usado pelo **XmlDocument** classe para localizar recursos que não são embutidos em dados XML, como o tipo de documento externo DTDs (definições), entidades e esquemas. Esses itens podem ser localizados em uma rede ou em uma unidade local, e são identificáveis por Uniform Resource Identifier (URI). Isso permite que o **XmlDocument** resolver **EntityReference** nós que estão presentes no documento e validar o documento de acordo com o esquema ou DTD externo.  
  
## <a name="fully-trusted-xmldocument"></a>XmlDocument totalmente confiável  
 O **XmlResolver** propriedade afeta a funcionalidade do **XmlDocument.Load** método. A tabela a seguir mostra como o **XmlDocument.XmlResolver** propriedade funciona quando o **XmlDocument** objeto é totalmente confiável. A tabela a seguir mostra o **XmlDocument.Load** métodos quando a entrada para a carga for um **TextReader**, **cadeia de caracteres**, **fluxo**, ou  **URI**. Esta tabela não é válido para o **carga** método se a **XmlDocument** é carregado de um **XmlReader**.  
  
|Propriedade de XmlResolver|Função|Observações|  
|--------------------------|--------------|-----------|  
|A propriedade é definida como um **XmlResolver** classe que foi criado anteriormente e possui propriedades já definidas pelo usuário.|O **XmlDocument** usa o **XmlResolver** que é fornecido para resolver nomes de arquivo, para resolver referências a recursos externos como DTDs, entidades e esquemas.<br /><br /> O **XmlResolver** também é usado quando Resolvendo recursos externos que são necessários para adicionar ou editar nós o **XmlDocument**.|O **XmlResolver** fornecido para o **XmlDocument** é o resolvedor é usado sempre que os recursos externos precisam ser localizado e resolvidos.|  
|A propriedade é definida como **nulo** (**nada** no Microsoft Visual Basic .NET).|Os recursos que exigem um recurso externo não são suportados, como localizar um esquema externo, ou o DTD. Nem as entidades externos serão resolvidas, e executar funções de edição, como inserir os nós de entidade que exigem resolução, não é suportado.|O **XmlDocument** carregamentos de arquivos como anônimos e não tenta resolver todos os outros recursos.|  
|A propriedade não está definida, mas esquerda em seu estado padrão.|Um **XmlUrlResolver** com NULL credenciais serão criadas e usadas pelo **XmlDocument** durante a resolução de nomes de arquivo, localizando DTDs, entidades e esquemas externos e **null** as credenciais são usadas durante a edição de nós.||  
  
 A tabela a seguir mostra o **XmlDocument.Load** método quando a entrada para o **carga** é um **XmlReader** e **XmlDocument** é totalmente confiável.  
  
|Propriedade de XmlResolver|Função|Observações|  
|--------------------------|--------------|-----------|  
|O **XmlResolver** classe usada pelo **XmlDocument** é a mesma classe que está sendo usada pelo **XmlReader**.|O **XmlDocument** usa o **XmlResolver** que foi atribuído para o **XmlReader**.<br /><br /> O **XmlDocument.Resolver** propriedade não pode ser definido, independentemente do **XmlDocument** nível, de confiança porque ele está ficando um **XmlResolver** do  **XmlReader**. Não é possível tentar substituir as configurações do **XmlReaders**' **XmlResolver** definindo o **XmlResolver** propriedade o **XmlDocument**.|O **XmlReader** pode ser o **XmlTextReader**, **XmlValidatingReader**, ou um leitor personalizados. Se o leitor usado oferece suporte a resolução de entidade, as entidades externos são resolvidas. Se o leitor passado não oferece suporte a referências a entidades, então as referências a entidades não são resolvidas.|  
  
## <a name="semi-trusted-xmldocument"></a>XmlDocument de confiança parcial  
 A tabela a seguir mostra como o **XmlDocument.XmlResolver** propriedade funciona quando o objeto é de confiança parcial. Esta tabela se aplica ao **XmlDocument.Load** métodos quando a entrada para a carga for um **TextReader**, **cadeia de caracteres**, **fluxo**, ou  **URI**. Esta tabela não é válido para o **carga** método se a **XmlDocument** é carregado de um **XmlReader**.  
  
|Propriedade de XmlResolver|Função|Observações|  
|--------------------------|--------------|-----------|  
|No cenário de confiança parcial, o **XmlResolver** propriedade não pode ser definida como algo diferente de null.|Um **XmlUrlResolver** com **nulo** credenciais serão criadas e usadas pelo **XmlDocument** durante a resolução de nomes de arquivo, localizando externos DTDs, entidades, e esquemas e **nulo** as credenciais são usadas durante a edição de nós.|Esse comportamento é idêntico ao comportamento quando o **XmlResolver** propriedade não é definida, mas deixada no estado padrão.<br /><br /> O **XmlDocument** usa permissões anônimas para todas as ações.|  
|A propriedade é definida como **nulo** (**nada** no Microsoft Visual Basic .NET).|Nenhum recurso que requer um recurso externo é suportado, como localizar um esquema externo ou um DTD. Nem as entidades externos serão resolvidas, e executar funções de edição como inserir os nós de entidade que exigem resolução, não é suportado.|Quando a propriedade for **nulo**, o comportamento é o mesmo independentemente do **XmlDocument** é totalmente confiável ou confiança parcial.|  
|A propriedade não está definida, mas esquerda em seu estado padrão.|Um **XmlUrlResolver** com **nulo** credenciais serão criadas e usadas pelo **XmlDocument** durante a resolução de nomes de arquivo, localizando externos DTDs, entidades, e esquemas e **nulo** as credenciais são usadas durante a edição de nós.|O **XmlDocument** usa permissões anônimas para todas as ações.|  
  
 Esta tabela se aplica ao **XmlDocument.Load** método quando a entrada para o **carga** é um **XmlReader**e o **XmlDocument** é confiança parcial.  
  
|Propriedade de XmlResolver|Função|Observações|  
|--------------------------|--------------|-----------|  
|O **XmlResolver** classe usada pelo **XmlDocument** é o mesmo que está sendo usado pelo **XmlReader**.|O **XmlDocument** usa o **XmlResolver** que foi atribuído para o **XmlReader**.<br /><br /> O **XmlDocument.Resolver** propriedade não pode ser definido, independentemente do **XmlDocument** nível, de confiança porque ele está ficando um **XmlResolver** do  **XmlReader**. Não é possível tentar substituir as configurações do **XmlReaders** **XmlResolver** definindo o **XmlResolver** propriedade o **XmlDocument**.|O **XmlReader** pode ser o **XmlTextReader**, validando <xref:System.Xml.XmlReader>, ou um leitor personalizados. Se o leitor usado oferece suporte a resolução de entidade, as entidades externos são resolvidas. Se o leitor passado não oferece suporte a referências a entidades, então as referências a entidades não são resolvidas.|  
  
 Defina o XmlResolver para conter as credenciais corretas permite acesso aos recursos externos.  
  
> [!NOTE]
>  Não é possível recuperar o **XmlResolver** propriedade. Isso ajuda a impedir que um usuário de reutilizar um **XmlResolver** em que credenciais foram definidas. Além disso, se um **XmlTextReader** ou validar <xref:System.Xml.XmlReader> é usado para carregar o **XmlDocument** e **XmlDocument** tem um resolvedor de tiver sido definido, os resolvedores de Esses leitores não são armazenados em cache pelo **XmlDocument** depois que o **carga** fase, já que isso também apresenta um risco de segurança.  
  
 Para obter mais informações, consulte a seção de Comentários da página de referência <xref:System.Xml.XmlResolver>.  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
