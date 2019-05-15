---
title: 'Mitigação: Desserialização de objetos em domínios do aplicativo'
ms.date: 03/30/2017
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd0cbd4c688815139d83a742bb75c54eebbe55b7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648470"
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a>Mitigação: Desserialização de objetos em domínios do aplicativo
Em alguns casos, quando um aplicativo usa dois ou mais domínios de aplicativo com bases de aplicativo diferentes, a tentativa de desserializar objetos no contexto da chamada lógica nos domínios de aplicativo aciona uma exceção.  
  
## <a name="diagnosing-the-issue"></a>Diagnosticar o problema  
 O problema surge na seguinte sequência de condições:  
  
1. Um aplicativo usa dois ou mais domínios de aplicativo com bases de aplicativo diferentes.  
  
2. Alguns tipos são adicionados explicitamente a <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> chamando-se um método como <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> ou <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>. Esses tipos não são marcados como serializáveis e não são armazenados no cache de assembly global.  
  
3. Mais tarde, a execução do código no domínio de aplicativo não padrão tenta ler um valor de um arquivo de configuração ou usar XML para desserializar um objeto.  
  
4. Para ler de um arquivo de configuração ou desserializar o objeto, um objeto <xref:System.Xml.XmlReader> tenta acessar o sistema de configuração.  
  
5. Se o sistema de configuração ainda não tiver sido inicializado, ele deverá concluir sua inicialização. Isso significa, entre outras coisas, que o tempo de execução precisa criar um caminho estável para um sistema de configuração, que faz o seguinte:  
  
    1. Ele procura a evidência do domínio de aplicativo não padrão.  
  
    2. Ele tentar calcular a evidência para o domínio de aplicativo não padrão com base no domínio de aplicativo padrão.  
  
    3. A chamada para obter a evidência do domínio de aplicativo padrão dispara uma chamada de domínio de aplicativo cruzado do domínio de aplicativo não padrão para o domínio de aplicativo padrão.  
  
    4. Como parte do contrato do domínio de aplicativo cruzado no .NET Framework, o conteúdo do contexto de chamada lógica também precisa de marshaling nos limites do domínio de aplicativo.  
  
6. Como os tipos que estão no contexto de chamada lógica não podem ser resolvidos no domínio de aplicativo padrão, uma exceção é acionada.  
  
## <a name="mitigation"></a>Redução  
 Para resolver esse problema, faça o seguinte  
  
1. Procure a chamada para `get_Evidence` na pilha de chamadas quando a exceção for acionada. A exceção pode ser qualquer uma do grande subconjunto de exceções, incluindo <xref:System.IO.FileNotFoundException> e <xref:System.Runtime.Serialization.SerializationException>.  
  
2. Identifique o local no aplicativo em que nenhum objeto é adicionado ao contexto de chamada lógica e adicione o seguinte código:  
  
    ```  
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Alterações no tempo de execução](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)
