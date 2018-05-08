---
title: Práticas recomendadas de confiança parcial
ms.date: 03/30/2017
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
ms.openlocfilehash: fca975ff4216384b970535273511eb07cd6ded68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="partial-trust-best-practices"></a>Práticas recomendadas de confiança parcial
Este tópico descreve as práticas recomendadas ao executar o Windows Communication Foundation (WCF) em um ambiente de confiança parcial.  
  
## <a name="serialization"></a>Serialização  
 Aplique as seguintes práticas ao usar o <xref:System.Runtime.Serialization.DataContractSerializer> em um aplicativo parcialmente confiável.  
  
-   Todos os tipos serializáveis devem ser marcados explicitamente com o `[DataContract]` atributo. As técnicas a seguir não têm suporte em um ambiente de confiança parcial:  
  
-   Marcação de classes para ser serializada com o <xref:System.SerializableAttribute>.  
  
-   Implementando o <xref:System.Runtime.Serialization.ISerializable> interface para permitir que uma classe controlar o processo de serialização.  
  
### <a name="using-datacontractserializer"></a>Usando o DataContractSerializer  
  
-   Todos os tipos marcados com o `[DataContract]` atributo deve ser público. Tipos não públicos não podem ser serializados em um ambiente de confiança parcial.  
  
-   Todos os `[DataContract]` membros em um serializável `[DataContract]` tipo deve ser público. Um tipo não público `[DataMember]` não pode ser serializado em um ambiente de confiança parcial.  
  
-   Os métodos que tratam os eventos de serialização (como `OnSerializing`, `OnSerialized`, `OnDeserializing`, e `OnDeserialized`) deve ser declarado como público. No entanto, as implementações explícitas e implícitas de <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> têm suporte.  
  
-   `[DataContract]` tipos implementados em assemblies marcados com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> não deve executar ações relacionadas à segurança no construtor de tipo, como o <xref:System.Runtime.Serialization.DataContractSerializer> não chamar o construtor do objeto recentemente criada durante a desserialização. Especificamente, as seguintes técnicas comuns de segurança devem ser evitadas para `[DataContract]` tipos:  
  
-   Tentativa de restringir o acesso de confiança parcial, tornando o construtor do tipo interno ou privado.  
  
-   Restringir o acesso ao tipo adicionando um `[LinkDemand]` para o construtor do tipo.  
  
-   Supondo que porque o objeto foi instanciado com êxito, qualquer impostas pelo construtor de verificações de validação passaram com êxito.  
  
### <a name="using-ixmlserializable"></a>Usando IXmlSerializable  
 Práticas recomendadas a seguir se aplicam a tipos que implementam <xref:System.Xml.Serialization.IXmlSerializable> e são serializados usando o <xref:System.Runtime.Serialization.DataContractSerializer>:  
  
-   O <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> implementações de método estático devem ser `public`.  
  
-   Os métodos de instância que implementam o <xref:System.Xml.Serialization.IXmlSerializable> interface deve ser `public`.  
  
## <a name="using-wcf-from-fully-trusted-platform-code-that-allows-calls-from-partially-trusted-callers"></a>Usando o WCF do código totalmente confiável de plataforma que permite chamadas de parcialmente confiável chamadores  
 O modelo de segurança de confiança parcial do WCF pressupõe que qualquer chamador de uma propriedade ou método público do WCF estiver sendo executado no contexto de segurança (ACS) de acesso de código, do aplicativo host. WCF também assume o contexto de segurança apenas um aplicativo existe para cada <xref:System.AppDomain>, e este contexto estabelecido em <xref:System.AppDomain> hora de criação por um host confiável (por exemplo, por uma chamada para <xref:System.AppDomain.CreateDomain%2A> ou pelo Gerenciador de aplicativos ASP.NET).  
  
 Esse modelo de segurança se aplica a aplicativos gravados pelo usuário que não é possível declarar permissões CAS adicionais, como o código do usuário em execução em um aplicativo ASP.NET de confiança média. No entanto, o código de plataforma totalmente confiáveis (por exemplo, um assembly de terceiros que está instalado no cache de assembly global e aceita chamadas de código parcialmente confiável) deve tomar cuidado explícito ao chamar WCF em nome de um aplicativo parcialmente confiável para Evite a introdução de vulnerabilidades de segurança de nível de aplicativo.  
  
 Código de confiança total evite alterar o conjunto de permissões de CAS do thread atual (chamando <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, ou <xref:System.Security.PermissionSet.Deny%2A>) antes de chamar APIs do WCF em nome de código parcialmente confiável. Declarando, negar ou caso contrário, criar um contexto de permissão de thread específica que é independente do contexto de segurança de nível de aplicativo pode resultar em comportamento inesperado. Dependendo do aplicativo, esse comportamento pode resultar em vulnerabilidades de segurança de nível de aplicativo.  
  
 Código que chama o WCF usando um contexto de permissões específicas de thread deve estar preparada para lidar com as seguintes situações podem ocorrer:  
  
-   O contexto de segurança específicas de thread não pode ser mantido para a duração da operação, o que resulta em exceções de segurança potencial.  
  
-   O código interno do WCF, bem como qualquer retornos de chamada fornecida pelo usuário podem ser executado em um contexto de segurança diferente daquele em que a chamada foi originalmente iniciada. Nesses contextos incluem:  
  
    -   O contexto de permissão do aplicativo.  
  
    -   Qualquer contexto específicas de thread permissão criado anteriormente por outros threads de usuário usados para chamar WCF durante o tempo de vida da execução no momento <xref:System.AppDomain>.  
  
 WCF garante que o código parcialmente confiável não pode obter permissões de confiança total, a menos que essas permissões são declaradas por um componente totalmente confiáveis antes de chamar APIs públicas do WCF. No entanto, eles não garantem que os efeitos de confiança total é isolado a um segmento específico, uma operação ou uma ação do usuário.  
  
 Como prática recomendada, evite criar contexto de permissões específicas de thread chamando <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.PermitOnly%2A>, ou <xref:System.Security.PermissionSet.Deny%2A>. Em vez disso, conceda ou negue o privilégio para o aplicativo em si, para que nenhum <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.PermissionSet.Deny%2A>, ou <xref:System.Security.PermissionSet.PermitOnly%2A> é necessário.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.Serialization.IXmlSerializable>
