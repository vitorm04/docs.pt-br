---
title: "Armazenamento local de thread: campos estáticos relativos a thread e slots de dados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], local storage
- threading [.NET Framework], thread-relative static fields
- local thread storage
- TLS
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 39dd80d378171563f2aadadaa146278e8a417d32
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>Armazenamento local de thread: campos estáticos relativos a thread e slots de dados
Você pode usar gerenciado armazenamento local de thread (TLS) para armazenar dados que seja exclusivo em um domínio de aplicativo e thread. O .NET Framework fornece duas maneiras de usar gerenciado TLS: slots dados e campos estáticos relativos a thread.  
  
-   Use campos estáticos relativos a thread (relativos a thread `Shared` campos no Visual Basic) se você puder prever suas necessidades exatas em tempo de compilação. Campos estáticos relativos a thread fornecem o melhor desempenho. Eles também oferecem os benefícios de verificação de tipo de tempo de compilação.  
  
-   Use os slots de dados quando os requisitos reais podem ser descobertos somente em tempo de execução. Slots de dados são mais lento e mais inadequado para uso de campos estáticos relativos a thread e dados são armazenados como tipo <xref:System.Object>, portanto, você deve convertê-lo para o tipo correto antes de você usá-lo.  
  
 Em C++ não gerenciado, você deve usar `TlsAlloc` alocar slots dinamicamente e `__declspec(thread)` para declarar que uma variável deve ser alocada no armazenamento relativos a thread. Slots dados e campos estáticos relativos a thread fornecem a versão gerenciada desse comportamento.  
  
 No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar o <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> classe para criar objetos de local de thread que são inicializados lentamente quando o objeto é consumido pela primeira vez. Para obter mais informações, veja [Inicialização lenta](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>Exclusividade dos dados no TLS gerenciado  
 Se você usar campos estáticos relativos a thread ou slots de dados, dados no TLS gerenciado são exclusivos para a combinação de domínio de aplicativo e o thread.  
  
-   Dentro de um domínio de aplicativo, um thread não é possível modificar os dados de outro thread, mesmo quando ambos os threads usam o mesmo campo ou um slot.  
  
-   Quando um thread acessa o mesmo campo ou o slot de vários domínios de aplicativo, um valor separado é mantido em cada domínio de aplicativo.  
  
 Por exemplo, se um thread define o valor de um campo estático relativos a thread, entra em outro domínio de aplicativo e, em seguida, recupera o valor do campo, o valor recuperado no segundo domínio de aplicativo é diferente do valor no primeiro domínio de aplicativo. Definindo um novo valor para o campo no segundo domínio de aplicativo não afeta o valor do campo no primeiro domínio de aplicativo.  
  
 Da mesma forma, quando um thread é o mesmo slot de dados nomeado em dois domínios diferentes, os dados no primeiro domínio de aplicativo permanecem independentemente dos dados no segundo domínio de aplicativo.  
  
## <a name="thread-relative-static-fields"></a>Campos estáticos relativos a thread  
 Se você souber que uma parte dos dados sempre é exclusiva para uma combinação de domínio de aplicativo e um thread, aplique a <xref:System.ThreadStaticAttribute> de atributo para o campo estático. Use o campo que você usaria qualquer outro campo estático. Os dados no campo são exclusivos para cada thread que utiliza.  
  
 Campos estáticos relativos a thread fornecem desempenho melhor que slots de dados e tem a vantagem de verificação de tipo de tempo de compilação.  
  
 Lembre-se de que qualquer código de construtor da classe será executado no primeiro segmento no contexto primeiro que acessa o campo. Em todos os outros segmentos ou contextos no mesmo domínio de aplicativo, os campos serão inicializados com `null` (`Nothing` no Visual Basic) se eles são tipos de referência ou para seu padrão valores se eles são os tipos de valor. Portanto, você não deve confiar em construtores de classe para inicializar campos estáticos relativos a thread. Em vez disso, evite inicializar campos estáticos relativos a thread e suponha que eles sejam inicializados para `null` (`Nothing`) ou para seus valores padrão.  
  
## <a name="data-slots"></a>Slots de dados  
 O .NET Framework fornece slots de dados dinâmicos que são exclusivos a uma combinação de thread e o domínio de aplicativo. Há dois tipos de slots de dados: chamada de slots e slots sem nome. Ambos são implementados usando o <xref:System.LocalDataStoreSlot> estrutura.  
  
-   Para criar um slot de dados nomeado, use o <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> ou <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> método. Para obter uma referência a um arquivo denominado slot, passe seu nome para o <xref:System.Threading.Thread.GetNamedDataSlot%2A> método.  
  
-   Para criar um slot de dados sem nome, use o <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> método.  
  
 Para ambos nome e sem nome slots, use o <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> e <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> métodos para definir e recuperar as informações no slot. Esses são os métodos estáticos que sempre atuam sobre os dados para o thread que está em execução-los.  
  
 Slots nomeados podem ser convenientes, porque você pode recuperar o slot quando necessário, passando o nome para o <xref:System.Threading.Thread.GetNamedDataSlot%2A> método, em vez de manter uma referência para um slot sem nome. No entanto, se outro componente usa o mesmo nome para seu armazenamento relativos a thread e um thread executa código do seu componente e o outro componente, os dois componentes podem corromper os dados do outro. (Este cenário pressupõe que ambos os componentes estão em execução no mesmo domínio do aplicativo e que eles não são projetados para compartilhar os mesmos dados.)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ContextStaticAttribute>  
 <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>  
 <xref:System.ThreadStaticAttribute>  
 <xref:System.Runtime.Remoting.Messaging.CallContext>  
 [Threading](../../../docs/standard/threading/index.md)
