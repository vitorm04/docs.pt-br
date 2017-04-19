---
title: "Alterações de tempo de execução no .NET Framework 4.5.1 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility
- runtime changes
- .NET Framework 4.5.1
ms.assetid: da880ad7-ba0a-4368-b340-705e3533c351
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4e4903c2f25354005f95b3ed8f9728cfe8a0a92e
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-451"></a>Alterações no tempo de execução no .NET Framework 4.5.1
Em casos raros, as alterações feitas no tempo de execução podem afetar aplicativos existentes que segmentam o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ou 4.5, mas são executados no tempo de execução do 4.51. Entre eles estão alterações feitas nas seguintes áreas:  
  
-   [Core](#Core)  
  
-   [WCF (Windows Communication Foundation)](#WCF)  
  
 A coluna Escopo nas tabelas a seguir especifica o significado de cada alteração:  
  
-   Principal. Uma alteração significativa que afeta um grande número de aplicativos ou que exige a modificação significativa do código. Observe que nenhuma das alterações feitas no tempo de execução entra nessa categoria.  
  
-   Secundário. Uma alteração que afeta um pequeno número de aplicativos ou que exige a modificação secundária do código.  
  
-   Borda. Uma alteração que afeta aplicativos em cenários muito específicos que não são comuns.  
  
-   Transparente. Uma alteração que não tem efeito visível para o desenvolvedor ou o usuário do aplicativo. O aplicativo não deve exigir modificação por conta dessa alteração.  
  
<a name="Core"></a>   
## <a name="core-runtime-changes"></a>Alterações feitas no tempo de execução básico  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Serialização <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>|Um objeto <xref:System.Collections.Concurrent.ConcurrentDictionary%602> serializado no .NET Framework 4.5 com o <xref:System.Runtime.Serialization.NetDataContractSerializer> não pode se desserializado no .NET Framework 4.5.1 e 4.5.2 apenas devido a alterações internas no tipo.<br /><br /> Essa alteração *não* se aplica aos seguintes cenários:<br /><br /> Um objeto <xref:System.Collections.Concurrent.ConcurrentDictionary%602> serializado no .NET Framework 4.5 e desserializado no [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. O <xref:System.Runtime.Serialization.NetDataContractSerializer> no [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] é capaz de desserializar o objeto.<br /><br /> Um objeto <xref:System.Collections.Concurrent.ConcurrentDictionary%602> serializado em uma versão posterior do .NET Framework e desserializado no .NET Framework 4.5. O <xref:System.Runtime.Serialization.NetDataContractSerializer> no .NET Framework 4.5 é capaz de desserializar o objeto.<br /><br /> Serialização e desserialização intraversões de um objeto <xref:System.Collections.Concurrent.ConcurrentDictionary%602> entre qualquer versão do .NET Framework após o .NET Framework 4.5. Essa alteração se aplica *somente* aos objetos serializados com o .NET Framework 4.5.|Duas soluções alternativas estarão disponíveis se for necessário serializar um objeto <xref:System.Collections.Concurrent.ConcurrentDictionary%602> no .NET Framework 4.5 e desserializá-lo em uma versão posterior do .NET Framework:<br /><br /> Use um serializador alternativo, como o <xref:System.Runtime.Serialization.DataContractSerializer> ou o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.<br /><br /> Faça upgrade para o [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], que dá suporte à desserialização do objeto <xref:System.Collections.Concurrent.ConcurrentDictionary%602> serializado com o .NET Framework 4.5.|Secundário|  
|Classe <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName>|<xref:System.Diagnostics.Tracing.EventListener> trunca cadeias de caracteres com nulos inseridos. A classe <xref:System.Diagnostics.Tracing.EventSource> não dá suporte a caracteres nulos.|A alteração afeta somente aplicativos que usam <xref:System.Diagnostics.Tracing.EventListener> para ler dados <xref:System.Diagnostics.Tracing.EventSource> em processo e que usam caracteres nulos como delimitadores.|Edge|  
|Classe <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>|O tempo de execução agora impõe o contrato que especifica o seguinte: uma classe derivada de <xref:System.Diagnostics.Tracing.EventSource> que define um método de evento ETW deve chamar a classe base <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=fullName> com a ID do evento seguida pelos mesmos argumentos que o método de evento ETW passou.|Uma exceção <xref:System.IndexOutOfRangeException> será gerada se um <xref:System.Diagnostics.Tracing.EventListener> ler os dados <xref:System.Diagnostics.Tracing.EventSource> em processo para uma origem de evento que viola esse contrato.<br /><br /> Confira [Mitigação: chamadas de método EventSource.WriteEvent](../../../docs/framework/migration-guide/mitigation-eventsource-writeevent-method-calls.md)|Secundário|  
|Desserialização de objetos em domínios de aplicativo|Em alguns casos, quando um aplicativo usa dois ou mais domínios de aplicativo com bases de aplicativo diferentes, a tentativa de desserializar objetos no contexto da chamada lógica nos domínios de aplicativo aciona uma exceção.|Esse problema surge em um cenário altamente específico. Para saber mais, confira [Mitigação: desserialização de objetos em domínios de aplicativos](../../../docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md).|Edge|  
|Método <xref:System.IO.Stream.Dispose%2A?displayProperty=fullName>|Em aplicativos da [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)], os adaptadores de fluxo do [!INCLUDE[wrt](../../../includes/wrt-md.md)] não chamam mais o método <xref:System.IO.Stream.FlushAsync%2A> do método <xref:System.IO.Stream.Dispose%2A>.|Essa alteração deve ser transparente. Os desenvolvedores podem restaurar o comportamento anterior gravando um código como este:<br /><br /> `using (System.IO.Stream stream = GetWindowsRuntimeStream() As Stream)  {     // do something     await stream.FlushAsync();   }`|Transparente|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf-runtime-changes"></a>Alterações feitas no tempo de execução do WCF (Windows Communication Foundation)  
  
|Recurso|Alteração|Impacto|Escopo|  
|-------------|------------|------------|-----------|  
|Definição de configuração [minFreeMemoryPercentageToActiveService](http://msdn.microsoft.com/library/ms731336.aspx)|A configuração estabelece a memória mínima que deve estar disponível no servidor para que um serviço WCF possa ser ativado. Ela foi desenvolvida para impedir exceções <xref:System.OutOfMemoryException>. No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], essa configuração não tinha nenhum efeito. No [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], a configuração é observada.|Ocorrerá uma exceção se a memória livre disponível no servidor Web for menor que a porcentagem definida pela definição de configuração. Alguns serviços WCF iniciados com êxito e executados em um ambiente de memória restrito agora podem falhar.<br /><br /> Confira [Mitigação: configuração minFreeMemoryPercentageToActiveService](../../../docs/framework/migration-guide/mitigation-minfreememorypercentagetoactiveservice-configuration-setting.md).|Secundário|  
  
## <a name="see-also"></a>Consulte também  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-5-1.md)   
 [Compatibilidade de aplicativos no 4.5](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [Compatibilidade de aplicativos no 4.5.2](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)
