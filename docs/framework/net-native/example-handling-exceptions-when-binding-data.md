---
title: 'Exemplo: lidar com exceções ao associar dados'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f7c40d1a179c29c3b92ca37848db6d1383e5d2d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049887"
---
# <a name="example-handling-exceptions-when-binding-data"></a><span data-ttu-id="0d141-102">Exemplo: lidar com exceções ao associar dados</span><span class="sxs-lookup"><span data-stu-id="0d141-102">Example: Handling Exceptions When Binding Data</span></span>
> [!NOTE]
> <span data-ttu-id="0d141-103">Este tópico refere-se ao Developer Preview do .NET Nativo, que é um software em pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="0d141-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="0d141-104">Você pode baixar a versão prévia do [site Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (registro obrigatório).</span><span class="sxs-lookup"><span data-stu-id="0d141-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="0d141-105">O exemplo a seguir mostra como resolver uma exceção [MissingMetadataException](missingmetadataexception-class-net-native.md) que é gerada quando um aplicativo compilado com a cadeia de ferramentas .net Native tenta associar dados.</span><span class="sxs-lookup"><span data-stu-id="0d141-105">The following example shows how to resolve a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception that is thrown when an app compiled with the .NET Native tool chain tries to bind data.</span></span> <span data-ttu-id="0d141-106">Aqui estão as informações da exceção:</span><span class="sxs-lookup"><span data-stu-id="0d141-106">Here’s the exception information:</span></span>  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 <span data-ttu-id="0d141-107">Esta é a pilha de chamadas associadas:</span><span class="sxs-lookup"><span data-stu-id="0d141-107">Here's the associated call stack:</span></span>  
  
```output
Reflection::Execution::ReflectionDomainSetupImplementation.CreateNonInvokabilityException+0x238  
Reflection::Core::ReflectionDomain.CreateNonInvokabilityException+0x2e  
Reflection::Core::Execution::ExecutionEnvironment.+0x316  
System::Reflection::Runtime::PropertyInfos::RuntimePropertyInfo.GetValue+0x1cb  
System::Reflection::PropertyInfo.GetValue+0x22  
System::Runtime::InteropServices::WindowsRuntime::CustomPropertyImpl.GetValue+0x42  
App!$66_Interop::McgNative.Func_IInspectable_IInspectable+0x158  
App!$66_Interop::McgNative::__vtable_Windows_UI_Xaml_Data__ICustomProperty.GetValue__STUB+0x46  
Windows_UI_Xaml!DirectUI::PropertyProviderPropertyAccess::GetValue+0x3f   
Windows_UI_Xaml!DirectUI::PropertyAccessPathStep::GetValue+0x31   
Windows_UI_Xaml!DirectUI::PropertyPathListener::ConnectPathStep+0x113  
```  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="0d141-108">O que o aplicativo estava fazendo?</span><span class="sxs-lookup"><span data-stu-id="0d141-108">What was the app doing?</span></span>  
 <span data-ttu-id="0d141-109">Na base da pilha, os quadros do <xref:Windows.UI.Xaml?displayProperty=nameWithType> namespace indicam que o mecanismo de renderização XAML estava em execução.</span><span class="sxs-lookup"><span data-stu-id="0d141-109">At the base of the stack, frames from the <xref:Windows.UI.Xaml?displayProperty=nameWithType> namespace indicate that the XAML rendering engine was running.</span></span>   <span data-ttu-id="0d141-110">O uso do método <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> indica uma pesquisa de reflexão do valor da propriedade no tipo cujos metadados foi removido.</span><span class="sxs-lookup"><span data-stu-id="0d141-110">The use of the <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> method indicates a reflection-based lookup of a property’s value on the type whose metadata was removed.</span></span>  
  
 <span data-ttu-id="0d141-111">A primeira etapa no fornecimento de uma diretiva de metadados seria adicionar metadados `serialize` ao tipo de forma que suas propriedades estejam acessíveis:</span><span class="sxs-lookup"><span data-stu-id="0d141-111">The first step in providing a metadata directive would be to add `serialize` metadata for the type so that its properties are all accessible:</span></span>  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="0d141-112">Esta é uma ocorrência isolada?</span><span class="sxs-lookup"><span data-stu-id="0d141-112">Is this an isolated case?</span></span>  
 <span data-ttu-id="0d141-113">Neste cenário, se a associação dos dados possuem metadados incompletos para um `ViewModel`, isso também pode ocorrer para outros.</span><span class="sxs-lookup"><span data-stu-id="0d141-113">In this scenario, if data binding has incomplete metadata for one `ViewModel`, it may for others, too.</span></span>  <span data-ttu-id="0d141-114">Se o código é estruturado de forma que os modelos de exibição do aplicativo estão todos no namespace `App.ViewModels`, você pode usar uma diretiva de tempo de execução mais geral:</span><span class="sxs-lookup"><span data-stu-id="0d141-114">If the code is structured in a way that the app’s view models are all in the `App.ViewModels` namespace, you could use a more general runtime directive:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a><span data-ttu-id="0d141-115">O código pode ser reconfigurado para não usar reflexão?</span><span class="sxs-lookup"><span data-stu-id="0d141-115">Could the code be rewritten to not use reflection?</span></span>  
 <span data-ttu-id="0d141-116">Como associação de dados possui reflexão intensa, alterar o código para evitar reflexão não é viável.</span><span class="sxs-lookup"><span data-stu-id="0d141-116">Because data binding is reflection-intensive, changing the code to avoid reflection isn’t feasible.</span></span>  
  
 <span data-ttu-id="0d141-117">No entanto, existem maneiras para especificar o `ViewModel` para a página XAML para que a cadeia de ferramentas possa associar propriedades de vinculação com o tipo correto no tempo de compilação e manter os metadados sem usar uma diretiva de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0d141-117">However, there are ways to specify the `ViewModel` to the XAML page so that the tool chain can associate property bindings with the correct type at compile time and keep the metadata without using a runtime directive.</span></span>  <span data-ttu-id="0d141-118">Por exemplo, você pode aplicar o <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> atributo em Propriedades.</span><span class="sxs-lookup"><span data-stu-id="0d141-118">For example, you could apply the <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> attribute on properties.</span></span> <span data-ttu-id="0d141-119">Isso faz com que o compilador XAML gere informações de pesquisa necessárias e evita que necessitem de uma diretiva de tempo de execução no arquivo Default.rd.xml.</span><span class="sxs-lookup"><span data-stu-id="0d141-119">This causes the XAML compiler to generate the required lookup information and avoids requiring a runtime directive in the Default.rd.xml file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d141-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d141-120">See also</span></span>

- [<span data-ttu-id="0d141-121">Introdução</span><span class="sxs-lookup"><span data-stu-id="0d141-121">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="0d141-122">Exemplo: Solucionando problemas de programação dinâmica</span><span class="sxs-lookup"><span data-stu-id="0d141-122">Example: Troubleshooting Dynamic Programming</span></span>](example-troubleshooting-dynamic-programming.md)
