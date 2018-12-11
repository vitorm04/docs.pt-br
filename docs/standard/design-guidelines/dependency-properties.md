---
title: Propriedades de Dependência
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
author: KrzysztofCwalina
ms.openlocfilehash: b577f42c98cb56fb367cb57a550cb094a8ef105e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145235"
---
# <a name="dependency-properties"></a>Propriedades de Dependência
Uma propriedade de dependência (DP) é uma propriedade regular que armazena o valor em um repositório de propriedades em vez de armazená-los em uma variável de tipo (campo), por exemplo.  
  
 Uma propriedade de dependência anexada é um tipo de propriedade de dependência modelado como métodos Get e Set estáticos que representa "propriedades", que descreve as relações entre objetos e seus contêineres (por exemplo, a posição de um `Button` do objeto em um `Panel` contêiner).  
  
 **✓ DO** fornecem as propriedades de dependência, se você precisar que as propriedades para oferecer suporte a recursos do WPF, como o estilo, gatilhos, associação de dados, animações, recursos dinâmicos e herança.  
  
## <a name="dependency-property-design"></a>Design de propriedade de dependência  
 **✓ DO** herdam <xref:System.Windows.DependencyObject>, ou um de seus subtipos, ao implementar propriedades de dependência. O tipo fornece uma implementação muito eficiente de um repositório de propriedades e automaticamente dá suporte à vinculação de dados do WPF.  
  
 **✓ DO** fornecem uma propriedade CLR e o campo estático público somente leitura armazenar uma instância de <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> para cada propriedade de dependência.  
  
 **✓ DO** implementar propriedades de dependência chamando métodos de instância <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> e <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.  
  
 **✓ DO** nome do campo de propriedade de dependência estática colocando o sufixo do nome da propriedade com "Property".  
  
 **X DO NOT** definir valores padrão das propriedades de dependência explicitamente no código; defini-las nos metadados.  
  
 Se você definir um padrão de propriedade explicitamente, poderá impedir que essa propriedade sendo definida por meios implícitos, como uma definição de estilo.  
  
 **X DO NOT** coloque o código nos acessadores de propriedade que não seja o código padrão para acessar o campo estático.  
  
 Que um código não será executado se a propriedade é definida por meios implícitos, como um estilo, porque a definição de estilo usa o campo estático diretamente.  
  
 **X DO NOT** usar propriedades de dependência para armazenar dados seguros. Propriedades de dependência até privados podem ser acessadas publicamente.  
  
## <a name="attached-dependency-property-design"></a>Design de propriedade de dependência anexada  
 Propriedades de dependência descritas na seção anterior representam propriedades intrínsecas do tipo declarativo; Por exemplo, o `Text` é uma propriedade do `TextButton`, que declara-o. Um tipo especial de propriedade de dependência é a propriedade de dependência anexada.  
  
 Um exemplo clássico de uma propriedade anexada é o <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> propriedade. A propriedade representa a posição da coluna do botão (não da grade), mas só é relevante se o botão está contido em uma grade e, portanto, ele é "anexado" a botões por grades.  
  
```xaml
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 A definição de uma propriedade anexada a aparência principalmente de uma propriedade de dependência normal, exceto que os acessadores são representados por métodos Get e Set estáticos:  
  
```csharp
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
 As propriedades geralmente implementam o que chamamos de validação. Lógica de validação é executada quando é feita uma tentativa para alterar o valor de uma propriedade.  
  
 Infelizmente, acessadores de propriedade de dependência não podem conter código de validação arbitrária. Em vez disso, lógica de validação de propriedade de dependência deve ser especificado durante o registro de propriedade.  
  
 **X DO NOT** colocar a lógica de validação de propriedade de dependência em acessadores de propriedade. Em vez disso, transmita um retorno de chamada de validação para `DependencyProperty.Register` método.  
  
## <a name="dependency-property-change-notifications"></a>Notificações de alteração de propriedade de dependência  
 **X DO NOT** implementar a lógica de notificação de alteração em acessadores de propriedade de dependência. Propriedades de dependência têm um recurso de notificações de alterações interno que deve ser usado, fornecendo um retorno de chamada de notificação de alteração para o <xref:System.Windows.PropertyMetadata>.  
  
## <a name="dependency-property-value-coercion"></a>Coerção de valor de propriedade de dependência  
 Coerção de propriedade ocorre quando o valor fornecido para um setter de propriedade é modificado por setter antes que o armazenamento de propriedades, na verdade, é modificado.  
  
 **X DO NOT** implementar a lógica de coerção em acessadores de propriedade de dependência.  
  
 Propriedades de dependência têm um recurso de coerção interna e ele pode ser usado ao fornecer um retorno de chamada de coerção para o `PropertyMetadata`.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
- [Padrões comuns de Design](../../../docs/standard/design-guidelines/common-design-patterns.md)
