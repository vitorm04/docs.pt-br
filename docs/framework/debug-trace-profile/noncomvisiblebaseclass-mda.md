---
title: MDA nonComVisibleBaseClass
description: Consulte o MDA (Assistente de depuração gerenciada) nonComVisibleBaseClass, que é invocado em chamadas de QueryInterface de código nativo falhando com COR_E_INVALIDOPERATION.
ms.date: 03/30/2017
helpviewer_keywords:
- visible classes
- managed debugging assistants (MDAs), COM visible classes
- nonComVisibleBaseClass MDA
- COM visible classes
- QueryInterface call failures
- MDAs (managed debugging assistants), COM visible classes
ms.assetid: 9ec1af27-604b-477e-9ee2-e833eb10d3ce
ms.openlocfilehash: 9f32b2c57f50fcd900b1fd78f4f8df1ec656a6db
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803906"
---
# <a name="noncomvisiblebaseclass-mda"></a><span data-ttu-id="7279f-103">MDA nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="7279f-103">nonComVisibleBaseClass MDA</span></span>
<span data-ttu-id="7279f-104">O MDA (Assistente de Depuração Gerenciado) de `nonComVisibleBaseClass` é ativado quando uma chamada `QueryInterface` é feita por código não gerenciado ou nativo no CCW (COM Callable Wrapper) de uma classe gerenciada visível em COM derivada de uma classe base que não é visível em COM.</span><span class="sxs-lookup"><span data-stu-id="7279f-104">The `nonComVisibleBaseClass` managed debugging assistant (MDA) is activated when a `QueryInterface` call is made by native or unmanaged code on the COM callable wrapper (CCW) of a COM-visible managed class that derives from a base class that is not COM visible.</span></span>  <span data-ttu-id="7279f-105">A chamada `QueryInterface` faz com que o MDA seja ativado apenas em casos nos quais a chamada solicita a interface de classe ou o `IDispatch` padrão da classe gerenciada visível em COM.</span><span class="sxs-lookup"><span data-stu-id="7279f-105">The `QueryInterface` call causes the MDA to activate only in cases where call requests the class interface or default `IDispatch` of the COM-visible managed class.</span></span>  <span data-ttu-id="7279f-106">O MDA não é ativado quando o `QueryInterface` é para uma interface explícita que tem o atributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> aplicado e é implementado explicitamente pela classe visível em COM.</span><span class="sxs-lookup"><span data-stu-id="7279f-106">The MDA is not activated when the `QueryInterface` is for an explicit interface that has the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute applied and is explicitly implemented by the COM-visible class.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7279f-107">Sintomas</span><span class="sxs-lookup"><span data-stu-id="7279f-107">Symptoms</span></span>  
 <span data-ttu-id="7279f-108">Uma chamada `QueryInterface` feita por meio do código nativo que está falhando com um HRESULT COR_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="7279f-108">A `QueryInterface` call made from native code that is failing with a COR_E_INVALIDOPERATION HRESULT.</span></span>  <span data-ttu-id="7279f-109">O HRESULT pode ser devido ao runtime não permitir chamadas `QueryInterface` que causariam a ativação desse MDA.</span><span class="sxs-lookup"><span data-stu-id="7279f-109">The HRESULT might be due to the runtime disallowing `QueryInterface` calls that would cause the activation of this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7279f-110">Causa</span><span class="sxs-lookup"><span data-stu-id="7279f-110">Cause</span></span>  
 <span data-ttu-id="7279f-111">O runtime não pode permitir chamadas `QueryInterface` para a interface de classe ou a interface `IDispatch` padrão de uma classe visível em COM que deriva de uma classe não visível em COM devido a possíveis problemas de controle de versão.</span><span class="sxs-lookup"><span data-stu-id="7279f-111">The runtime cannot allow `QueryInterface` calls for the class interface or default `IDispatch` interface of a COM-visible class that derives from a class that is not COM-visible because of potential versioning problems.</span></span>  <span data-ttu-id="7279f-112">Por exemplo, se os membros públicos foram adicionados à a classe base que não é visível em COM, os clientes COM existentes usando a classe derivada podem ser interrompidos porque a vtable da classe derivada, que contém os membros da classe base, seria modificada por uma alteração desse tipo.</span><span class="sxs-lookup"><span data-stu-id="7279f-112">For example, if any public members were added to the base class that is not COM-visible, existing COM clients using the derived class could potentially break because the vtable of the derived class, which contains the base class members, would be altered by such a change.</span></span>  <span data-ttu-id="7279f-113">Interfaces explícitas expostas a COM não têm esse problema porque elas não incluem os membros base das interfaces na vtable.</span><span class="sxs-lookup"><span data-stu-id="7279f-113">Explicit interfaces exposed to COM do not have this problem because they do not include the base members of interfaces in the vtable.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7279f-114">Resolução</span><span class="sxs-lookup"><span data-stu-id="7279f-114">Resolution</span></span>  
 <span data-ttu-id="7279f-115">Não expor a interface de classe.</span><span class="sxs-lookup"><span data-stu-id="7279f-115">Do not expose the class interface.</span></span> <span data-ttu-id="7279f-116">Definir uma interface explícita e aplicar o atributo <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> a ele.</span><span class="sxs-lookup"><span data-stu-id="7279f-116">Define an explicit interface and apply the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribute to it.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7279f-117">Efeito sobre o runtime</span><span class="sxs-lookup"><span data-stu-id="7279f-117">Effect on the Runtime</span></span>  
 <span data-ttu-id="7279f-118">Esse MDA não tem efeito sobre o CLR.</span><span class="sxs-lookup"><span data-stu-id="7279f-118">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7279f-119">Saída</span><span class="sxs-lookup"><span data-stu-id="7279f-119">Output</span></span>  
 <span data-ttu-id="7279f-120">A seguir está um exemplo de mensagem para uma chamada `QueryInterface` em uma classe visível em COM `Derived` que deriva de uma classe não visível em COM `Base`.</span><span class="sxs-lookup"><span data-stu-id="7279f-120">The following is an example message for a `QueryInterface` call on a COM-visible class `Derived` that derives from a non-COM-visible class `Base`.</span></span>  
  
```output
A QueryInterface call was made requesting the class interface of COM
visible managed class 'Derived'. However since this class derives from
non COM visible class 'Base', the QueryInterface call will fail. This
is done to prevent the non COM visible base class from being
constrained by the COM versioning rules.
```  
  
## <a name="configuration"></a><span data-ttu-id="7279f-121">Configuração</span><span class="sxs-lookup"><span data-stu-id="7279f-121">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <nonComVisibleBaseClass />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7279f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7279f-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="7279f-123">Diagnosticando erros com assistentes para depuração gerenciada</span><span class="sxs-lookup"><span data-stu-id="7279f-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="7279f-124">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="7279f-124">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
