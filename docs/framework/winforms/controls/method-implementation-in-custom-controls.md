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
ms.openlocfilehash: 38dcad25af31b87afc1cc6ef4f89a1f7903bc0ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117411"
---
# <a name="method-implementation-in-custom-controls"></a><span data-ttu-id="290e5-102">Implementação do método em controles personalizados</span><span class="sxs-lookup"><span data-stu-id="290e5-102">Method Implementation in Custom Controls</span></span>
<span data-ttu-id="290e5-103">Um método é implementado em um controle da mesma maneira que seria em qualquer outro componente.</span><span class="sxs-lookup"><span data-stu-id="290e5-103">A method is implemented in a control in the same manner a method would be implemented in any other component.</span></span>  
  
 <span data-ttu-id="290e5-104">No Visual Basic, se for necessário a um método retornar um valor, será implementado como um `Public Function`.</span><span class="sxs-lookup"><span data-stu-id="290e5-104">In Visual Basic, if a method is required to return a value, it is implemented as a `Public Function`.</span></span> <span data-ttu-id="290e5-105">Se nenhum valor for retornado, será implementado como um `Public Sub`.</span><span class="sxs-lookup"><span data-stu-id="290e5-105">If no value is returned, it is implemented as a `Public Sub`.</span></span> <span data-ttu-id="290e5-106">Métodos são declarados usando a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="290e5-106">Methods are declared using the following syntax:</span></span>  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 <span data-ttu-id="290e5-107">Como funções retornam um valor, devem especificar um tipo de retorno, como inteiro, cadeia de caracteres, objeto e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="290e5-107">Because functions return a value, they must specify a return type, such as integer, string, object, and so on.</span></span> <span data-ttu-id="290e5-108">Os argumentos `Function` ou `Sub` que os procedimentos tomam, quando houver, também devem ser especificados.</span><span class="sxs-lookup"><span data-stu-id="290e5-108">The arguments `Function` or `Sub` procedures take, if any, must also be specified.</span></span>  
  
 <span data-ttu-id="290e5-109">O C# não distingue entre funções e procedimentos, como o Visual Basic faz.</span><span class="sxs-lookup"><span data-stu-id="290e5-109">C# makes no distinction between functions and procedures, as Visual Basic does.</span></span> <span data-ttu-id="290e5-110">Um método retorna um valor ou um `void`.</span><span class="sxs-lookup"><span data-stu-id="290e5-110">A method either returns a value or returns `void`.</span></span> <span data-ttu-id="290e5-111">A sintaxe para declarar um método público em C# é:</span><span class="sxs-lookup"><span data-stu-id="290e5-111">The syntax for declaring a C# public method is:</span></span>  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 <span data-ttu-id="290e5-112">Ao declarar um método, declare todos os seus argumentos como tipos de dados explícitos sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="290e5-112">When you declare a method, declare all of its arguments as explicit data types whenever possible.</span></span> <span data-ttu-id="290e5-113">Argumentos que tomam referências de objetos devem ser declarados como tipos de classe específicos — por exemplo, `As Widget` ao invés de `As Object`.</span><span class="sxs-lookup"><span data-stu-id="290e5-113">Arguments that take object references should be declared as specific class types — for example, `As Widget` instead of `As Object`.</span></span> <span data-ttu-id="290e5-114">No Visual Basic, a configuração padrão `Option Strict` impõe essa regra automaticamente.</span><span class="sxs-lookup"><span data-stu-id="290e5-114">In Visual Basic, the default setting `Option Strict` automatically enforces this rule.</span></span>  
  
 <span data-ttu-id="290e5-115">Argumentos digitados permitem a captura de muitos erros do desenvolvedor pelo compilador, ao invés de em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="290e5-115">Typed arguments allow many developer errors to be caught by the compiler, rather than at run time.</span></span> <span data-ttu-id="290e5-116">O compilador sempre captura erros, enquanto o teste de tempo de execução é apenas tão bom quanto o conjunto de testes.</span><span class="sxs-lookup"><span data-stu-id="290e5-116">The compiler always catches errors, whereas run-time testing is only as good as the test suite.</span></span>  
  
## <a name="overloaded-methods"></a><span data-ttu-id="290e5-117">Métodos Sobrecarregados</span><span class="sxs-lookup"><span data-stu-id="290e5-117">Overloaded Methods</span></span>  
 <span data-ttu-id="290e5-118">Se desejar permitir aos usuários de seu controle fornecer diferentes combinações de parâmetros a um método, forneça múltiplas sobrecargas do método, usando tipos de dados explícitos.</span><span class="sxs-lookup"><span data-stu-id="290e5-118">If you want to allow users of your control to supply different combinations of parameters to a method, provide multiple overloads of the method, using explicit data types.</span></span> <span data-ttu-id="290e5-119">Evite criar parâmetros declarados `As Object` que podem conter qualquer tipo de dados, pois isso pode levar a erros que podem não ser capturados no teste.</span><span class="sxs-lookup"><span data-stu-id="290e5-119">Avoid creating parameters declared `As Object` that can contain any data type, as this can lead to errors that might not be caught in testing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="290e5-120">O tipo de dados universal no Common Language Runtime é `Object` ao invés de `Variant`.</span><span class="sxs-lookup"><span data-stu-id="290e5-120">The universal data type in the common language runtime is `Object` rather than `Variant`.</span></span> `Variant` <span data-ttu-id="290e5-121">Ele foi removido do idioma.</span><span class="sxs-lookup"><span data-stu-id="290e5-121">has been removed from the language.</span></span>  
  
 <span data-ttu-id="290e5-122">Por exemplo, o `Spin` método de um controle `Widget` hipotético poderá permitir especificação direta de velocidade e direção da rotação ou especificação de outro `Widget` objeto do qual o momentum angular deve ser absorvido:</span><span class="sxs-lookup"><span data-stu-id="290e5-122">For example, the `Spin` method of a hypothetical `Widget` control might allow either direct specification of spin direction and speed, or specification of another `Widget` object from which angular momentum is to be absorbed:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="290e5-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="290e5-123">See also</span></span>

- [<span data-ttu-id="290e5-124">Eventos</span><span class="sxs-lookup"><span data-stu-id="290e5-124">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="290e5-125">Propriedades em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="290e5-125">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
