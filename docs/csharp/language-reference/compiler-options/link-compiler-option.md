---
title: "-link (Opções do compilador do C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- /l compiler option [C#]
- /link compiler option [C#]
- -l compiler option [C#]
- EmbedInteropTypes
- l compiler option [C#]
- embed interop types [COM Interop]
- -link compiler option [C#]
- link compiler option [C#]
ms.assetid: 00da70c6-9ea1-43c2-86f2-aa7f26c03475
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3096dd622a0b7c5fae13412a95322b934bd38b76
ms.lasthandoff: 03/13/2017

---
# <a name="link-c-compiler-options"></a>/link (opções do compilador C#)
Faz com que o compilador disponibilize as informações de tipo COM nos assemblies especificados para o projeto sendo compilado no momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/link:fileList  
// -or-  
/l:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Necessário. Lista delimitada por vírgulas de nomes de arquivo do assembly. Se o nome do arquivo contém um espaço, coloque o nome entre aspas.  
  
## <a name="remarks"></a>Comentários  
 A opção `/link` permite que você implante um aplicativo que inseriu informações de tipo. O aplicativo pode usar tipos em um assembly de tempo de execução que implementa as informações de tipo inseridas sem a necessidade de uma referência ao assembly de tempo de execução. Se forem publicadas várias versões do assembly de tempo de execução, o aplicativo que contém as informações de tipo inseridas poderá trabalhar com as várias versões sem precisar ser recompilado. Para obter um exemplo, consulte [Instruções passo a passo: Inserindo tipos de assemblies gerenciado](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
 Usar a opção `/link` é especialmente útil quando você está trabalhando com a interoperabilidade COM. Você pode inserir tipos COM para que seu aplicativo não precise mais de um PIA (assembly de interoperabilidade primário) no computador de destino. A opção `/link` instrui o compilador a inserir as informações de tipo de COM do assembly de interoperabilidade referenciado no código compilado resultante. O tipo COM é identificado pelo valor CLSID (GUID). Como resultado, o aplicativo pode ser executado em um computador de destino que tem os mesmos tipos COM instalados com os mesmos valores CLSID. Os aplicativos que automatizam o Microsoft Office são um bom exemplo. Como aplicativos como o Office normalmente mantêm o mesmo valor CLSID entre diferentes versões, seu aplicativo pode usar os tipos COM referenciados contanto que o .NET Framework 4 ou posterior esteja instalado no computador de destino e seu aplicativo use métodos, propriedades ou eventos que estão incluídos nos tipos COM referenciados.  
  
 A opção `/link` incorpora apenas interfaces, estruturas e delegados. Não há suporte para a inserção de classes COM.  
  
> [!NOTE]
>  Quando você cria uma instância de um tipo COM inserido no seu código, você deve criar a instância usando a interface apropriada. Tentar criar uma instância de um tipo COM inserido usando o CoClass causa um erro.  
  
 Para definir a opção `/link` em [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], adicione uma referência de assembly e defina a propriedade `Embed Interop Types` como **true**. O valor padrão da propriedade `Embed Interop Types` é **false**.  
  
 Se você vincular a um assembly COM (Assembly A) que em si faz referência a outro assembly COM (Assembly B), também precisará vincular ao Assembly B se uma das seguintes opções for verdadeira:  
  
-   Um tipo do Assembly A herda de um tipo ou implementa uma interface do Assembly B.  
  
-   Um campo, propriedade, evento ou método que tem um tipo de retorno ou de parâmetro do Assembly B é invocado.  
  
 Como a opção do compilador [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md), a opção do compilador `/link` usa o arquivo de resposta Csc.rsp, que faz referência a assemblies [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] usados com frequência. Use a opção do compilador [/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) se não desejar que o compilador use o arquivo Csc.rsp.  
  
 A forma abreviada de `/link` é `/l`.  
  
## <a name="generics-and-embedded-types"></a>Tipos genéricos e inseridos  
 As seções a seguir descrevem as limitações no uso de tipos genéricos em aplicativos que inserem tipos de interoperabilidade.  
  
### <a name="generic-interfaces"></a>Interfaces genéricas  
 As interfaces genéricas que são inseridas de um assembly de interoperabilidade não podem ser usadas. Isso é mostrado no exemplo a seguir.  
  
 [!code-cs[VbLinkCompilerCS#1](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_1.cs)]  
  
### <a name="types-that-have-generic-parameters"></a>Tipos que têm parâmetros genéricos  
 Os tipos que têm um parâmetro genérico cujo tipo é inserido de um assembly de interoperabilidade não poderão ser usados se o tipo for de um assembly externo. Essa restrição não se aplica a interfaces. Por exemplo, considere a interface <xref:Microsoft.Office.Interop.Excel.Range> que é definida no assembly <xref:Microsoft.Office.Interop.Excel>. Se uma biblioteca insere tipos de interoperabilidade do assembly <xref:Microsoft.Office.Interop.Excel> e expõe um método que retorna um tipo genérico que tem um parâmetro cujo tipo é a interface <xref:Microsoft.Office.Interop.Excel.Range>, esse método deve retornar uma interface genérica, como mostrado no exemplo de código a seguir.  
  
 [!code-cs[VbLinkCompilerCS#2](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_2.cs)]  
[!code-cs[VbLinkCompilerCS#3](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_3.cs)]  
[!code-cs[VbLinkCompilerCS#4](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_4.cs)]  
  
 No exemplo a seguir, o código do cliente pode chamar o método que retorna a interface genérica <xref:System.Collections.IList> sem erros.  
  
 [!code-cs[VbLinkCompilerCS#5](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_5.cs)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila o arquivo de origem `OfficeApp.cs` e faz referência aos assemblies de `COMData1.dll` e `COMData2.dll` para produzir `OfficeApp.exe`.  
  
```csharp  
csc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Instruções passo a passo: Inserindo tipos de assemblies gerenciados](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)   
 [/reference (opções do compilador do C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)   
 [/noconfig (opções do compilador do C#)](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)   
 [Compilação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [Visão geral sobre interoperabilidade](../../../csharp/programming-guide/interop/interoperability-overview.md)
