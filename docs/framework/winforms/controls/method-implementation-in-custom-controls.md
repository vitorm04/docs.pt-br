---
title: "Implementação do método em controles personalizados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c992197b653fb3999870247a3a4cdb4015612ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
>  O tipo de dados universal no Common Language Runtime é `Object` ao invés de `Variant`. `Variant`foi removido do idioma.  
  
 Por exemplo, o `Spin` método de um hipotético `Widget` controle pode permitir que a especificação direta de direção de rotação e velocidade ou especificação de outro `Widget` objeto do qual impulso angular será absorvidos:  
  
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
 [Eventos](../../../../docs/standard/events/index.md)  
 [Propriedades em controles dos Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
