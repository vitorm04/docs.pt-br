---
title: Retornos de chamada da propriedade de dependência e validação
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], validation
- coerce value callbacks [WPF]
- callbacks [WPF], validation
- dependency properties [WPF], callbacks
- validation of dependency properties [WPF]
ms.assetid: 48db5fb2-da7f-49a6-8e81-3540e7b25825
ms.openlocfilehash: 7f00961ba100700c68936cc33facfdc758c77d3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940819"
---
# <a name="dependency-property-callbacks-and-validation"></a>Retornos de chamada da propriedade de dependência e validação
Este tópico descreve como criar propriedades de dependência usando implementações alternativas personalizadas para recursos relacionados a propriedade como validação de determinação, callbacks que são chamadas sempre que o valor efetivo da propriedade é alterado e substituindo possíveis influências externas na determinação do valor. Este tópico também aborda os cenários em que é apropriado expandir os comportamentos padrões do sistema usando essas técnicas.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Este tópico pressupõe que você compreenda os cenários básicos de implementar uma propriedade de dependência e como os metadados são aplicados a uma propriedade de dependência personalizada. Consulte [Propriedades de dependência personalizadas](custom-dependency-properties.md) e [Metadados de propriedade de dependência](dependency-property-metadata.md) para ver o contexto.  
  
<a name="Validation_Callbacks"></a>   
## <a name="validation-callbacks"></a>Retornos de chamadas de validação  
 Retornos de chamada de validação podem ser atribuídos a uma propriedade de dependência quando você registra-a primeiro. O retorno de chamada de validação não faz parte dos metadados de propriedade; é uma entrada direta do <xref:System.Windows.DependencyProperty.Register%2A> método. Portanto, depois de criar um retorno de chamada de validação para uma propriedade de dependência, ela não pode ser substituída por uma nova implementação.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Os retornos de chamada são implementados, de modo que eles recebem um valor de objeto. Elas retornam `true` se o valor fornecido é válido para a propriedade; caso contrário, eles retornam `false`. Supõe-se que a propriedade é do tipo correto de acordo com o tipo registrado no sistema de propriedade, então a verificação de tipo dentro de retornos de chamada normalmente não é feita. Os retornos de chamada são usados pelo sistema de propriedades em uma variedade de operações diferentes. Isso inclui a inicialização de tipo inicial por valor padrão, alteração programática invocando <xref:System.Windows.DependencyObject.SetValue%2A>ou tentativas de substituição de metadados com o novo valor padrão fornecido. Se o retorno de chamada de validação é chamado por qualquer uma dessas operações e retorna `false`, em seguida, uma exceção será gerada. Criadores de aplicativo devem estar preparados para tratar essas exceções. Um uso comum de retornos de chamada de validação é validar valores de enumeração ou restrição de valores de números inteiros ou duplos quando a propriedade define as medidas que devem ser zero ou maior.  
  
 Retornos de chamada de validação são projetados especificamente para ser validadores de classe, não validadores de instância. Os parâmetros do retorno de chamada não comunicam um <xref:System.Windows.DependencyObject> específico no qual as propriedades a serem validadas são definidas. Portanto, os retornos de chamada de validação não são úteis para aplicar as possíveis "dependências" que podem influenciar a um valor da propriedade, no qual o valor específico de instância de uma propriedade é dependente de fatores como valores específicos de instância de outras propriedades ou estado de tempo de execução.  
  
 Veja a seguir um exemplo de código para um cenário de retorno de chamada de validação muito simples: Validando que <xref:System.Double> uma propriedade que <xref:System.Double.PositiveInfinity> é <xref:System.Double.NegativeInfinity>digitada como primitiva não é ou.  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>   
## <a name="coerce-value-callbacks-and-property-changed-events"></a>Forçar retornos de chamada de valor e eventos alterados de propriedade  
 Os retornos de chamada de valor forçado passam <xref:System.Windows.DependencyObject> a instância específica para propriedades, <xref:System.Windows.PropertyChangedCallback> como as implementações que são invocadas pelo sistema de propriedades sempre que o valor de uma propriedade de dependência é alterado. Ao usar esses dois retornos de chamada em combinação, você pode criar uma série de propriedades nos elementos em que alterações em uma propriedade forçará uma coerção ou reavaliação de outra propriedade.  
  
 Um cenário típico para usar uma ligação de propriedades de dependência é quando você tem uma propriedade controlada por interface do usuário no qual o elemento contém uma propriedade para o valor mínimo e máximo e uma terceira propriedade para o valor real ou atual. Aqui, se o máximo foi ajustado de tal forma que o valor atual excedeu o novo máximo, você pode querer forçar o valor atual a não ser maior do que o novo máximo e um relacionamento análogo para mínimo e atual.  
  
 A seguir está um breve exemplo de código para apenas uma das três propriedades de dependência que ilustram esse relacionamento. O exemplo mostra como a propriedade `CurrentReading` de um conjunto Mín/Máx/atual das *propriedades de leitura relacionadas está registrado. Ele usa a validação como mostrado na seção anterior.  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 O retorno de chamada de propriedade alterada para Atual é usado para encaminhar a alteração para outras propriedades dependentes, invocando explicitamente os retornos de chamada de valores que estão registrados para as outras propriedades:  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 Os retornos de chamada de valor forçados verificam os valores das propriedades das quais a propriedade atual está potencialmente dependente e converte o valor atual se necessário:  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
> Valores padrão das propriedades não são forçados. Um valor de propriedade igual ao valor padrão pode ocorrer se um valor de propriedade ainda tiver seu padrão inicial ou por meio da limpeza de <xref:System.Windows.DependencyObject.ClearValue%2A>outros valores com.  
  
 Os retornos de chamada de propriedade alterada e forçados fazem parte dos metadados da propriedade. Portanto, você pode alterar os retornos de chamada para uma determinada propriedade de dependência, pois ela existe em um tipo que você deriva do tipo que possui a propriedade de dependência, substituindo os metadados por essa propriedade em seu tipo.  
  
<a name="Advanced"></a>   
## <a name="advanced-coercion-and-callback-scenarios"></a>Coerção avançada e cenários de retorno de chamada  
  
### <a name="constraints-and-desired-values"></a>Restrições e valores desejados  
 Os <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> retornos de chamada serão usados pelo sistema de propriedades para forçar um valor de acordo com a lógica que você declarar, mas um valor forçado de uma propriedade de conjunto localmente ainda manterá um "valor desejado" internamente. Se as restrições são baseadas em outros valores de propriedade isso pode ser alterado dinamicamente durante o tempo de vida do aplicativo, as restrições de coerção são alteradas dinamicamente também e a propriedade restrita poderá alterar seu valor para chegar o mais perto possível do valor desejado dadas as novas restrições. O valor se tornará o valor desejado se todas as restrições forem respeitadas. Você poderá potencialmente criar algumas situações de dependência bastante complicadas se você tiver várias propriedades que são dependentes entre si, de maneira circular. Por exemplo, no cenário de Min/máx/atual, você pode optar por mínimo e máximo ser configurável pelo usuário. Nesse caso, você precisará forçar que o máximo seja sempre maior que o mínimo e vice-versa. Mas se essa coerção estiver ativa e o máximo é forçado para o mínimo, isso deixará Atual em um estado instável, porque ele é dependente de ambos e é restrito ao intervalo entre os valores, que é zero. Em seguida, se o valor máximo ou mínimo for ajustado, atual parecerá "seguir" um dos valores, porque o valor desejado de atual ainda está armazenado e está tentando atingir o valor desejado conforme as restrições são relaxadas.  
  
 Não há nada tecnicamente errado com dependências complexas, mas podem ser um ponto prejudicial no desempenho se elas exigem um grande número de reavaliações e também podem ser confusas para os usuários se afetam a interface do usuário diretamente. Tenha cuidado com a propriedade alterada e os retornos de chamada de valor e certifique-se de que a coerção que está sendo tentada pode ser tratada como sem ambiguidade possível e sem "restrições em excesso".  
  
### <a name="using-coercevalue-to-cancel-value-changes"></a>Usando CoerceValue para cancelar as alterações de valor  
 O sistema de propriedades tratará <xref:System.Windows.CoerceValueCallback> qualquer um que retorna <xref:System.Windows.DependencyProperty.UnsetValue> o valor como um caso especial. Esse caso especial significa que a alteração de propriedade que resultou na <xref:System.Windows.CoerceValueCallback> chamada deve ser rejeitada pelo sistema de propriedades e que o sistema de propriedades deve reportar qualquer valor anterior que a propriedade tivesse. Esse mecanismo poderá ser útil para verificar se as alterações a uma propriedade que foram iniciadas de forma assíncrona ainda são válidas para o estado atual do objeto e para eliminar as alterações se não forem válidas. Outro cenário possível é que você pode seletivamente suprimir um valor dependendo de qual componente de determinação do valor da propriedade é responsável pelo valor que está sendo relatado. Para fazer isso, você pode usar o <xref:System.Windows.DependencyProperty> passado no retorno de chamada e o identificador de propriedade como <xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A>entrada para e depois processar <xref:System.Windows.ValueSource>o.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral das propriedades da dependência](dependency-properties-overview.md)
- [Metadados de propriedade da dependência](dependency-property-metadata.md)
- [Propriedades de dependência personalizada](custom-dependency-properties.md)
