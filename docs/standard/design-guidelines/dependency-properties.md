---
title: "Propriedades de Dependência"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 21e2026e7ce0f2dcf1ffc9a328b1bb9630cd8fbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="dependency-properties"></a>Propriedades de Dependência
Uma propriedade de dependência (DP) é uma propriedade que armazena o valor em um repositório de propriedades em vez de fazê-lo em uma variável de tipo (campo), por exemplo.  
  
 Uma propriedade de dependência anexado é um tipo de propriedade de dependência modelada como métodos Get e Set estáticos que representa "propriedades", que descrevem relações entre seus contêineres e objetos (por exemplo, a posição de um `Button` do objeto em um `Panel` contêiner).  
  
 **FAZER ✓** fornecem as propriedades de dependência, se você precisar que as propriedades para oferecer suporte a recursos do WPF, como o estilo, gatilhos, associação de dados, animações, recursos dinâmicos e herança.  
  
## <a name="dependency-property-design"></a>Design de propriedade de dependência  
 **FAZER ✓** herdam <xref:System.Windows.DependencyObject>, ou um de seus subtipos, ao implementar propriedades de dependência. O tipo fornece uma implementação muito eficiente de um repositório de propriedade e automaticamente dá suporte à associação de dados do WPF.  
  
 **FAZER ✓** fornecem uma propriedade CLR e o campo estático público somente leitura armazenar uma instância de <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> para cada propriedade de dependência.  
  
 **FAZER ✓** implementar propriedades de dependência chamando métodos de instância <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> e <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.  
  
 **FAZER ✓** nome do campo de propriedade de dependência estática colocando o sufixo do nome da propriedade com "Property".  
  
 **X não** definir valores padrão das propriedades de dependência explicitamente no código; defini-las nos metadados.  
  
 Se você definir um padrão de propriedade explicitamente, você pode impedir que essa propriedade sendo definida de alguma maneira implícita, como um estilo.  
  
 **X não** coloque o código nos acessadores de propriedade que não seja o código padrão para acessar o campo estático.  
  
 Se código não irá executar se a propriedade é definida por meio de implícita, como um estilo, porque o estilo usa o campo estático diretamente.  
  
 **X não** usar propriedades de dependência para armazenar dados seguros. Propriedades de dependência até mesmo podem ser acessadas publicamente.  
  
## <a name="attached-dependency-property-design"></a>Design de propriedade de dependência anexado  
 Propriedades de dependência descritas na seção anterior representam propriedades intrínsecas do tipo de declaração; Por exemplo, o `Text` é uma propriedade do `TextButton`, que declara. Um tipo especial de propriedade de dependência é a propriedade de dependência anexado.  
  
 É um exemplo clássico de uma propriedade anexada a <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> propriedade. A propriedade representa a posição de coluna do botão (não da grade), mas só será relevante se o botão estiver contido em uma grade e, portanto, é "anexado" a botões pela grade.  
  
```  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 A definição de uma propriedade anexada aparência principalmente de uma propriedade de dependência normal, exceto que os acessadores são representados por métodos estáticos Get e Set:  
  
```  
public class Grid {  
  
    public static int GetColumn(DependencyObject obj) {  
        return (int)obj.GetValue(ColumnProperty);  
    }  
  
    public static void SetColumn(DependencyObject obj, int value) {  
        obj.SetValue(ColumnProperty,value);  
    }  
  
    public static readonly DependencyProperty ColumnProperty =  
        DependencyProperty.RegisterAttached(  
            "Column",  
            typeof(int),  
            typeof(Grid)  
    );  
}  
```  
  
## <a name="dependency-property-validation"></a>Validação de propriedade de dependência  
 Propriedades geralmente implementam o que é chamado de validação. Lógica de validação é executada quando é feita uma tentativa de alterar o valor de uma propriedade.  
  
 Infelizmente acessadores de propriedade de dependência não podem conter código de validação arbitrária. Em vez disso, lógica de validação de propriedade de dependência deve ser especificado durante o registro de propriedade.  
  
 **X não** colocar a lógica de validação de propriedade de dependência em acessadores de propriedade. Em vez disso, passar um retorno de chamada de validação para `DependencyProperty.Register` método.  
  
## <a name="dependency-property-change-notifications"></a>Notificações de alteração de propriedade de dependência  
 **X não** implementar a lógica de notificação de alteração em acessadores de propriedade de dependência. Propriedades de dependência tem um recurso de notificações de alteração interna que deve ser usado, fornecendo um retorno de chamada de notificação de alteração para o <xref:System.Windows.PropertyMetadata>.  
  
## <a name="dependency-property-value-coercion"></a>Coerção de valor de propriedade de dependência  
 Coerção de propriedade ocorre quando o valor fornecido para um setter de propriedade for modificado pela setter antes que o armazenamento de propriedades, na verdade, é modificado.  
  
 **X não** implementar a lógica de coerção em acessadores de propriedade de dependência.  
  
 Propriedades de dependência tem um recurso de coerção interna e ele pode ser usado, fornecendo um retorno de chamada de coerção para o `PropertyMetadata`.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Padrões comuns de Design](../../../docs/standard/design-guidelines/common-design-patterns.md)
