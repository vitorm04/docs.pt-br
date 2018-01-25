---
title: "Objetos extensíveis"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords: extensible objects [WCF]
ms.assetid: bc88cefc-31fb-428e-9447-6d20a7d452af
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a1bb341d9e164b1ce232f238f8ddf4a0cf807363
ms.sourcegitcommit: c1904b0437605a90e5aa65b4abd7e048000e349d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2018
---
# <a name="extensible-objects"></a>Objetos extensíveis
O padrão de objeto extensível é usado para estender as classes de tempo de execução existentes com a nova funcionalidade ou para adicionar o novo estado para um objeto. Extensões, anexadas a um dos objetos extensíveis, habilitar comportamentos em diferentes estágios de processamento para acessar o estado compartilhado e anexado a um objeto extensível comum que eles possam acessar a funcionalidade.  
  
## <a name="the-iextensibleobjectt-pattern"></a>O IExtensibleObject\<T > padrão  
 Existem três interfaces no padrão de objeto extensível: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, e <xref:System.ServiceModel.IExtensionCollection%601>.  
  
 O <xref:System.ServiceModel.IExtensibleObject%601> interface é implementada por tipos que permitem <xref:System.ServiceModel.IExtension%601> objetos para personalizar sua funcionalidade.  
  
 Objetos extensíveis permitem agregação dinâmica de <xref:System.ServiceModel.IExtension%601> objetos. <xref:System.ServiceModel.IExtension%601>objetos são caracterizados por interface a seguir:  
  
```  
public interface IExtension<T>  
where T : IExtensibleObject<T>  
{  
    void Attach(T owner);  
    void Detach(T owner);  
}  
```  
  
 A restrição de tipo garante que as extensões só podem ser definidas para as classes que são <xref:System.ServiceModel.IExtensibleObject%601>. <xref:System.ServiceModel.IExtension%601.Attach%2A>e <xref:System.ServiceModel.IExtension%601.Detach%2A> fornecer notificação de agregação ou disaggregation.  
  
 Ele é válido para implementações restringir quando eles podem ser adicionados e removidos de um proprietário. Por exemplo, você pode não permitir remoção totalmente, não permitindo adicionar ou remover extensões quando o proprietário ou a extensão estiver em um determinado estado, não permitir adição simultaneamente para vários proprietários ou permitir apenas uma única adição seguida por uma única de remoção.  
  
 <xref:System.ServiceModel.IExtension%601>não significa que todas as interações com outras interfaces gerenciadas padrão. Especificamente, o <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> método no objeto do proprietário não desanexar normalmente suas extensões.  
  
 Quando uma extensão é adicionada à coleção, <xref:System.ServiceModel.IExtension%601.Attach%2A> é chamado antes que ele vai para a coleção. Quando uma extensão é removida da coleção, <xref:System.ServiceModel.IExtension%601.Detach%2A> é chamado depois que ele é removido. Isso significa (supondo que a sincronização apropriado) uma extensão pode contar encontrados somente na coleção enquanto ele está entre <xref:System.ServiceModel.IExtension%601.Attach%2A> e <xref:System.ServiceModel.IExtension%601.Detach%2A>.  
  
 O objeto passado para <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> ou <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> não precisa ser <xref:System.ServiceModel.IExtension%601> (por exemplo, você pode passar qualquer objeto), mas a extensão retornada é um <xref:System.ServiceModel.IExtension%601>.  
  
 Se nenhuma extensão na coleção é um <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> retorna null, e <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> retorna uma coleção vazia. Se implementam várias extensões <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> retorna um deles. O valor retornado de <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> é um instantâneo.
  
 Há dois cenários principais. O primeiro cenário usa o <xref:System.ServiceModel.IExtensibleObject%601.Extensions%2A> a propriedade como um dicionário baseada no tipo para inserir o estado em um objeto para outro componente procurá-lo usando o tipo de habilitar.  
  
 O segundo cenário usa o <xref:System.ServiceModel.IExtension%601.Attach%2A> e <xref:System.ServiceModel.IExtension%601.Detach%2A> propriedades para permitir que um objeto participe de comportamento personalizado, como registrar-se para eventos, observar as transições de estado e assim por diante.  
  
 O <xref:System.ServiceModel.IExtensionCollection%601> interface é uma coleção do <xref:System.ServiceModel.IExtension%601> objetos que permitem a recuperação de <xref:System.ServiceModel.IExtension%601> por seu tipo. <xref:System.ServiceModel.IExtensionCollection%601.Find%2A?displayProperty=nameWithType>Retorna o último adicionado objeto que é um <xref:System.ServiceModel.IExtension%601> desse tipo.  
  
### <a name="extensible-objects-in-windows-communication-foundation"></a>Objetos extensíveis no Windows Communication Foundation  
 Há quatro objetos extensíveis em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]:  
  
-   <xref:System.ServiceModel.ServiceHostBase>– Esta é a classe base para o host do serviço.  Extensões dessa classe podem ser usadas para estender o comportamento do <xref:System.ServiceModel.ServiceHostBase> si mesmo ou para armazenar o estado de cada serviço.  
  
-   <xref:System.ServiceModel.InstanceContext>– Essa classe se conecta a uma instância do tipo de serviço com o tempo de execução do serviço.  Ele contém informações sobre a instância, bem como uma referência para o <xref:System.ServiceModel.InstanceContext>contendo <xref:System.ServiceModel.ServiceHostBase>. Extensões dessa classe podem ser usadas para estender o comportamento do <xref:System.ServiceModel.InstanceContext> ou para armazenar o estado de cada serviço.  
  
-   <xref:System.ServiceModel.OperationContext>– Essa classe representa as informações de operação que coleta o tempo de execução para cada operação.  Isso inclui informações como os cabeçalhos de mensagem de entrada, as propriedades de mensagem de entrada, a identidade de segurança de entrada e outras informações.  Extensões dessa classe podem estender o comportamento de <xref:System.ServiceModel.OperationContext> ou armazenar o estado de cada operação.  
  
-   <xref:System.ServiceModel.IContextChannel>– Essa interface permite a inspeção de cada estado para os canais e proxies compilados pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tempo de execução.  Extensões dessa classe podem estender o comportamento de <xref:System.ServiceModel.IClientChannel> ou pode ser usado para armazenar o estado de cada canal.  
  
-  
  
 O exemplo de código a seguir mostra o uso de uma extensão de simple para rastrear <xref:System.ServiceModel.InstanceContext> objetos.  
  
 [!code-csharp[IInstanceContextInitializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/iinstancecontextinitializer/cs/initializer.cs#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.IExtensibleObject%601>  
 <xref:System.ServiceModel.IExtension%601>  
 <xref:System.ServiceModel.IExtensionCollection%601>
