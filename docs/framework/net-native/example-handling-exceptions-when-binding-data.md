---
title: 'Exemplo: lidando com exceções ao associar dados'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89e7a0929bd5f07c5a1986d885984332d692d3a9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43867111"
---
# <a name="example-handling-exceptions-when-binding-data"></a>Exemplo: lidando com exceções ao associar dados
> [!NOTE]
>  Este tópico refere-se ao Developer Preview do .NET Nativo, que é um software em pré-lançamento. Você pode baixar a versão prévia do [site Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (registro obrigatório).  
  
 O exemplo a seguir mostra como resolver uma exceção [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) gerada quando um aplicativo compilado com a cadeia de ferramentas do [!INCLUDE[net_native](../../../includes/net-native-md.md)] tenta associar dados. Aqui estão as informações da exceção:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 Esta é a pilha de chamadas associadas:  
  
```  
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
  
## <a name="what-was-the-app-doing"></a>O que o aplicativo estava fazendo?  
 Na base da pilha, os quadros do namespace [Windows.UI.Xaml](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.aspx) indicam que o mecanismo de renderização de XAML estava em execução.   O uso do método <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> indica uma pesquisa de reflexão do valor da propriedade no tipo cujos metadados foi removido.  
  
 A primeira etapa no fornecimento de uma diretiva de metadados seria adicionar metadados `serialize` ao tipo de forma que suas propriedades estejam acessíveis:  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>Esta é uma ocorrência isolada?  
 Neste cenário, se a associação dos dados possuem metadados incompletos para um `ViewModel`, isso também pode ocorrer para outros.  Se o código é estruturado de forma que os modelos de exibição do aplicativo estão todos no namespace `App.ViewModels`, você pode usar uma diretiva de tempo de execução mais geral:  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>O código pode ser reconfigurado para não usar reflexão?  
 Como associação de dados possui reflexão intensa, alterar o código para evitar reflexão não é viável.  
  
 No entanto, existem maneiras para especificar o `ViewModel` para a página XAML para que a cadeia de ferramentas possa associar propriedades de vinculação com o tipo correto no tempo de compilação e manter os metadados sem usar uma diretiva de tempo de execução.  Por exemplo, você pode aplicar o [Windows.UI.Xaml.Data.BindableAttribute](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.bindableattribute.aspx) atributo a propriedades. Isso faz com que o compilador XAML gere informações de pesquisa necessárias e evita que necessitem de uma diretiva de tempo de execução no arquivo Default.rd.xml.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Exemplo: solução de problemas de programação dinâmica](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)
