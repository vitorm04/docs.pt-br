---
title: Práticas recomendadas de confiança parcial
ms.date: 03/30/2017
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
ms.openlocfilehash: c83c36020cfd5b41e99ff9eeb7968d0b5df909a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769454"
---
# <a name="partial-trust-best-practices"></a>Práticas recomendadas de confiança parcial
Este tópico descreve as práticas recomendadas ao executar o Windows Communication Foundation (WCF) em um ambiente de confiança parcial.  
  
## <a name="serialization"></a>Serialização  
 Aplique as seguintes práticas ao usar o <xref:System.Runtime.Serialization.DataContractSerializer> em um aplicativo parcialmente confiável.  
  
- Todos os tipos serializáveis devem ser marcados explicitamente com o `[DataContract]` atributo. As técnicas a seguir não têm suporte em um ambiente de confiança parcial:  
  
- Marcação de classes a serem serializados com o <xref:System.SerializableAttribute>.  
  
- Implementando o <xref:System.Runtime.Serialization.ISerializable> interface para permitir que uma classe controlar seu processo de serialização.  
  
### <a name="using-datacontractserializer"></a>Usando o DataContractSerializer  
  
- Todos os tipos marcados com o `[DataContract]` atributo deve ser público. Tipos não públicos não podem ser serializados em um ambiente de confiança parcial.  
  
- Todos os `[DataContract]` membros em um serializável `[DataContract]` tipo deve ser público. Um tipo com não-públicos `[DataMember]` não pode ser serializado em um ambiente de confiança parcial.  
  
- Métodos que manipulam os eventos de serialização (como `OnSerializing`, `OnSerialized`, `OnDeserializing`, e `OnDeserialized`) deve ser declarado como público. No entanto, as implementações explícitas e implícitas de <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> têm suporte.  
  
- `[DataContract]` tipos implementados em assemblies marcados com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> não deve executar ações relacionadas à segurança no construtor de tipo, como o <xref:System.Runtime.Serialization.DataContractSerializer> não chama o construtor do objeto de uma instância recém-criada durante a desserialização. Especificamente, as seguintes técnicas comuns de segurança devem ser evitadas para `[DataContract]` tipos:  
  
- Tentativa de restringir o acesso de confiança parcial, tornando o construtor do tipo interno ou privado.  
  
- Restringindo o acesso ao tipo, adicionando um `[LinkDemand]` para o construtor do tipo.  
  
- Supondo que porque o objeto foi instanciado com êxito, nenhuma verificação de validação imposta pelo construtor passaram com êxito.  
  
### <a name="using-ixmlserializable"></a>Usando IXmlSerializable  
 As práticas recomendadas a seguir se aplicam para tipos que implementam <xref:System.Xml.Serialization.IXmlSerializable> e são serializados usando a <xref:System.Runtime.Serialization.DataContractSerializer>:  
  
- O <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> implementações de método estático devem ser `public`.  
  
- Os métodos de instância que implementam o <xref:System.Xml.Serialization.IXmlSerializable> interface deve ser `public`.  
  
## <a name="using-wcf-from-fully-trusted-platform-code-that-allows-calls-from-partially-trusted-callers"></a>Usando o WCF a partir do código totalmente confiável de plataforma que permite chamadas de parcialmente confiável para os chamadores  
 O modelo de segurança de confiança parcial do WCF pressupõe que qualquer chamador de um método público de WCF ou a propriedade está em execução no contexto de CAS (segurança) de acesso do código do aplicativo host. O WCF também assume que esse contexto de segurança de apenas um aplicativo existe para cada <xref:System.AppDomain>, e esse contexto estabelecido em <xref:System.AppDomain> hora de criação por um host confiável (por exemplo, por uma chamada para <xref:System.AppDomain.CreateDomain%2A> ou pelo Gerenciador de aplicativos ASP.NET).  
  
 Esse modelo de segurança se aplica a aplicativos escritos pelo usuário que não é possível declarar permissões CAS adicionais, como o código do usuário em execução em um aplicativo ASP.NET de confiança médio. No entanto, o código de plataforma de totalmente confiável (por exemplo, um assembly de terceiros que está instalado no cache de assembly global e aceita chamadas de código parcialmente confiável) deve tomar o cuidado explícito ao chamar ao WCF em nome de um aplicativo parcialmente confiável para Evite introduzir vulnerabilidades de segurança de nível de aplicativo.  
  
 Código de confiança total deve evitar alterar o conjunto de permissões de CAS do thread atual (chamando <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, ou <xref:System.Security.PermissionSet.Deny%2A>) antes de chamar as APIs do WCF em nome do código parcialmente confiável. Declarando, negar ou caso contrário, a criação de um contexto de permissão específicas de thread que é independente do contexto de segurança de nível de aplicativo pode resultar em comportamento inesperado. Dependendo do aplicativo, esse comportamento pode resultar em vulnerabilidades de segurança de nível de aplicativo.  
  
 Código que chamadas ao WCF usando um contexto de permissão específicas de thread devem estar preparadas para lidar com as seguintes situações que podem surgir:  
  
- O contexto de segurança específicas de thread não pode ser mantido para a duração da operação, o que resulta em exceções de segurança potenciais.  
  
- Código interno do WCF, bem como qualquer retorno de chamada fornecido pelo usuário podem ser executadas em um contexto de segurança diferente em que a chamada foi originalmente iniciada. Esses contextos incluem:  
  
    - O contexto de permissão do aplicativo.  
  
    - Qualquer contexto de permissão específicas de thread criado anteriormente por outros threads de usuário usados para chamar ao WCF durante o tempo de vida da execução no momento <xref:System.AppDomain>.  
  
 WCF garante que o código parcialmente confiável não pode obter permissões de confiança total, a menos que essas permissões são declaradas por um componente totalmente confiável antes de chamar em APIs públicas do WCF. No entanto, ele não garante que os efeitos de declarando confiança total é isolada em um thread específico, a operação ou a ação do usuário.  
  
 Como uma prática recomendada, evite criar contexto de permissão específicas de thread chamando <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, ou <xref:System.Security.PermissionSet.Deny%2A>. Em vez disso, conceder ou negar o privilégio para o aplicativo em si, para que nenhum <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.Deny%2A>, ou <xref:System.Security.PermissionSet.PermitOnly%2A> é necessária.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
