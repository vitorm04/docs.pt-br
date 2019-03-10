---
title: Implementação do método em controles personalizados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], method implementation
- custom controls [Windows Forms], overloading methods
- custom controls [Windows Forms], method implementation
- methods [Windows Forms]
- methods [Windows Forms], custom controls
ms.assetid: 35d14fca-4bb4-4a27-8211-1f7a98ea27de
ms.openlocfilehash: 5bcc6441ab1a615c31a5a028fc7f8f09cbdd4c10
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710362"
---
# <a name="method-implementation-in-custom-controls"></a>Implementação do método em controles personalizados
Um método é implementado em um controle da mesma maneira que seria em qualquer outro componente.  
  
 No Visual Basic, se for necessário a um método retornar um valor, será implementado como um `Public Function`. Se nenhum valor for retornado, será implementado como um `Public Sub`. Métodos são declarados usando a seguinte sintaxe:  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 Como funções retornam um valor, devem especificar um tipo de retorno, como inteiro, cadeia de caracteres, objeto e assim por diante. Os argumentos `Function` ou `Sub` que os procedimentos tomam, quando houver, também devem ser especificados.  
  
 O C# não distingue entre funções e procedimentos, como o Visual Basic faz. Um método retorna um valor ou um `void`. A sintaxe para declarar um método público em C# é:  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 Ao declarar um método, declare todos os seus argumentos como tipos de dados explícitos sempre que possível. Argumentos que tomam referências de objetos devem ser declarados como tipos de classe específicos — por exemplo, `As Widget` ao invés de `As Object`. No Visual Basic, a configuração padrão `Option Strict` impõe essa regra automaticamente.  
  
 Argumentos digitados permitem a captura de muitos erros do desenvolvedor pelo compilador, ao invés de em tempo de execução. O compilador sempre captura erros, enquanto o teste de tempo de execução é apenas tão bom quanto o conjunto de testes.  
  
## <a name="overloaded-methods"></a>Métodos Sobrecarregados  
 Se desejar permitir aos usuários de seu controle fornecer diferentes combinações de parâmetros a um método, forneça múltiplas sobrecargas do método, usando tipos de dados explícitos. Evite criar parâmetros declarados `As Object` que podem conter qualquer tipo de dados, pois isso pode levar a erros que podem não ser capturados no teste.  
  
> [!NOTE]
>  O tipo de dados universal no Common Language Runtime é `Object` ao invés de `Variant`. `Variant` foi removido do idioma.  
  
 Por exemplo, o `Spin` método de um controle `Widget` hipotético poderá permitir especificação direta de velocidade e direção da rotação ou especificação de outro `Widget` objeto do qual o momentum angular deve ser absorvido:  
  
```vb  
Overloads Public Sub Spin( _  
   ByVal SpinDirection As SpinDirectionsEnum, _  
   ByVal RevolutionsPerSecond As Double)  
   ' Implementation code here.  
End Sub  
Overloads Public Sub Spin(ByVal Driver As Widget) _  
   ' Implementation code here.  
End Sub  
```  
  
```csharp  
public void Spin(SpinDirectionsEnum spinDirection, double revolutionsPerSecond)  
{  
   // Implementation code here.  
}  
  
public void Spin(Widget driver)  
{  
   // Implementation code here.  
}  
```  
  
## <a name="see-also"></a>Consulte também
- [Eventos](../../../standard/events/index.md)
- [Propriedades em controles do Windows Forms](properties-in-windows-forms-controls.md)
