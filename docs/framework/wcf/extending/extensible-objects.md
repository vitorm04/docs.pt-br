---
title: Objetos extensíveis
ms.date: 03/30/2017
helpviewer_keywords:
- extensible objects [WCF]
ms.assetid: bc88cefc-31fb-428e-9447-6d20a7d452af
ms.openlocfilehash: 1af44f2394bbf27f9219831612b4e73d7a1759e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220273"
---
# <a name="extensible-objects"></a>Objetos extensíveis
O padrão de objeto extensível é usado para estender as classes de tempo de execução existentes com a nova funcionalidade ou para adicionar o novo estado a um objeto. Extensões, anexadas a um dos objetos extensíveis, habilitar comportamentos em muito diferentes estágios de processamento para acessar o estado compartilhado e a funcionalidade anexada a um objeto extensível comum que eles podem acessar.  
  
## <a name="the-iextensibleobjectt-pattern"></a>O IExtensibleObject\<T > padrão  
 Existem três interfaces no padrão de objeto extensível: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, e <xref:System.ServiceModel.IExtensionCollection%601>.  
  
 O <xref:System.ServiceModel.IExtensibleObject%601> interface é implementada pelos tipos que permitem <xref:System.ServiceModel.IExtension%601> objetos para personalizar sua funcionalidade.  
  
 Objetos extensíveis permitem agregação dinâmica de <xref:System.ServiceModel.IExtension%601> objetos. <xref:System.ServiceModel.IExtension%601> objetos são caracterizados pela interface a seguir:  
  
```  
public interface IExtension<T>  
where T : IExtensibleObject<T>  
{  
    void Attach(T owner);  
    void Detach(T owner);  
}  
```  
  
 A restrição de tipo garante que as extensões só podem ser definidas para classes que são <xref:System.ServiceModel.IExtensibleObject%601>. <xref:System.ServiceModel.IExtension%601.Attach%2A> e <xref:System.ServiceModel.IExtension%601.Detach%2A> fornecem notificação de agregação ou disaggregation.  
  
 Ele é válido para implementações para restringir quando eles podem ser adicionados e removidos de um proprietário. Por exemplo, você pode não permitir remoção totalmente, não permitindo adicionando ou removendo extensões quando o proprietário ou a extensão estiver em um determinado estado, não permitir adicionando simultaneamente para vários proprietários ou permitir que apenas uma única adição seguida por uma única de remoção.  
  
 <xref:System.ServiceModel.IExtension%601> não implica em todas as interações com outras interfaces gerenciadas padrão. Especificamente, o <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> método no objeto do proprietário não desanexar normalmente suas extensões.  
  
 Quando uma extensão é adicionada à coleção, <xref:System.ServiceModel.IExtension%601.Attach%2A> é chamado antes que ele vai para a coleção. Quando uma extensão é removida da coleção, <xref:System.ServiceModel.IExtension%601.Detach%2A> é chamado depois que ele é removido. Isso significa (supondo que a sincronização apropriado) uma extensão pode contar com encontrados somente na coleção enquanto ele está entre <xref:System.ServiceModel.IExtension%601.Attach%2A> e <xref:System.ServiceModel.IExtension%601.Detach%2A>.  
  
 O objeto passado para <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> ou <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> não precisam ser <xref:System.ServiceModel.IExtension%601> (por exemplo, você pode passar qualquer objeto), mas a extensão retornada é um <xref:System.ServiceModel.IExtension%601>.  
  
 Se nenhuma extensão na coleção é um <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> retorna null, e <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> retorna uma coleção vazia. Se várias extensões de implementam <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> retorne uma delas. O valor retornado de <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> é um instantâneo.
  
 Há dois cenários principais. O primeiro cenário usa o <xref:System.ServiceModel.IExtensibleObject%601.Extensions%2A> a propriedade como um dicionário com base no tipo para inserir o estado em um objeto para habilitar outro componente procurá-lo usando o tipo.  
  
 O segundo cenário usa o <xref:System.ServiceModel.IExtension%601.Attach%2A> e <xref:System.ServiceModel.IExtension%601.Detach%2A> propriedades permitem que um objeto participe de comportamento personalizado, como se registrar para eventos, observar as transições de estado, e assim por diante.  
  
 O <xref:System.ServiceModel.IExtensionCollection%601> interface é uma coleção do <xref:System.ServiceModel.IExtension%601> objetos que permitem a recuperação de <xref:System.ServiceModel.IExtension%601> por seu tipo. <xref:System.ServiceModel.IExtensionCollection%601.Find%2A?displayProperty=nameWithType> Retorna mais recentemente adicionado o objeto que é um <xref:System.ServiceModel.IExtension%601> desse tipo.  
  
### <a name="extensible-objects-in-windows-communication-foundation"></a>Objetos extensíveis no Windows Communication Foundation  
 Há quatro objetos extensíveis no Windows Communication Foundation (WCF):  
  
-   <xref:System.ServiceModel.ServiceHostBase> -Esta é a classe base para o host do serviço.  Extensões dessa classe podem ser usadas para estender o comportamento do <xref:System.ServiceModel.ServiceHostBase> em si ou para armazenar o estado para cada serviço.  
  
-   <xref:System.ServiceModel.InstanceContext> – Essa classe se conecta a uma instância do tipo de serviço com o tempo de execução do serviço.  Ele contém informações sobre a instância, bem como uma referência para o <xref:System.ServiceModel.InstanceContext>que contém <xref:System.ServiceModel.ServiceHostBase>. Extensões dessa classe podem ser usadas para estender o comportamento do <xref:System.ServiceModel.InstanceContext> ou para armazenar o estado para cada serviço.  
  
-   <xref:System.ServiceModel.OperationContext> – Essa classe representa as informações de operação que coleta de tempo de execução para cada operação.  Isso inclui informações como os cabeçalhos de mensagem de entrada, as propriedades de mensagem de entrada, a identidade de segurança de entrada e outras informações.  Extensões dessa classe podem estender o comportamento de <xref:System.ServiceModel.OperationContext> ou armazenar o estado para cada operação.  
  
-   <xref:System.ServiceModel.IContextChannel> – Essa interface permite a inspeção do estado de cada para os canais e proxies criados pelo runtime do WCF.  Extensões dessa classe podem estender o comportamento de <xref:System.ServiceModel.IClientChannel> ou pode usá-lo para armazenar o estado de cada canal.  
  
-  
  
 O exemplo de código a seguir mostra o uso de uma extensão simple para acompanhar <xref:System.ServiceModel.InstanceContext> objetos.  
  
 [!code-csharp[IInstanceContextInitializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/iinstancecontextinitializer/cs/initializer.cs#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.IExtensibleObject%601>
- <xref:System.ServiceModel.IExtension%601>
- <xref:System.ServiceModel.IExtensionCollection%601>
