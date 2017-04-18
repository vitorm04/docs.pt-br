---
title: /link (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e98c855f0a0185e9d1b6682df9fc734e9f1f07bc
ms.lasthandoff: 03/13/2017

---
# <a name="link-visual-basic"></a>/link (Visual Basic)
Faz com que o compilador disponibilizar informações de tipo COM nos assemblies especificados para o projeto que você está compilando atualmente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/link:fileList  
' -or-  
/l:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`fileList`|Necessário. Lista delimitada por vírgulas de nomes de arquivo de assembly. Se o nome do arquivo contém um espaço, coloque o nome entre aspas.|  
  
## <a name="remarks"></a>Comentários  
 O `/link` opção permite que você implantar um aplicativo que incorporou informações de tipo. O aplicativo pode usar tipos em um assembly de tempo de execução que implementam as informações de tipo inserido sem a necessidade de uma referência ao assembly de tempo de execução. Se várias versões do assembly em tempo de execução são publicadas, o aplicativo que contém as informações de tipo inserido pode trabalhar com várias versões sem precisar ser recompilado. Para obter um exemplo, consulte [passo a passo: inserindo tipos de Assemblies gerenciados](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
 Usando o `/link` opção é especialmente útil quando você está trabalhando com interoperabilidade COM. Você pode inserir tipos COM para que seu aplicativo não exige um assembly de interoperabilidade primária (PIA) no computador de destino. O `/link` opção instrui o compilador a inserir as informações de tipo de COM do assembly referenciado interoperabilidade no código compilado resultante. O tipo COM é identificado pelo valor CLSID (GUID). Como resultado, o aplicativo pode ser executado em um computador de destino que tenha instalado os mesmos tipos COM os mesmos valores CLSID. Os aplicativos que automatizam o Microsoft Office são um bom exemplo. Como aplicativos como o Office normalmente mantêm o mesmo valor CLSID entre diferentes versões, seu aplicativo pode usar tipos referenciados COM longa como .NET Framework 4 ou posterior estiver instalada no computador de destino e seu aplicativo usa métodos, propriedades ou eventos que estão incluídos nos tipos referenciados COM.  
  
 O `/link` opção incorpora apenas interfaces, estruturas e delegados. Não há suporte para a incorporação de classes COM.  
  
> [!NOTE]
>  Quando você cria uma instância de um tipo COM inserido no seu código, você deve criar a instância usando a interface apropriada. Tentativa de criar uma instância de um tipo COM inserido usando o CoClass causa um erro.  
  
 Para definir o `/link` opção [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], adicione uma referência de assembly e defina o `Embed Interop Types` propriedade **true**. O padrão para o `Embed Interop Types` é de propriedade **false**.  
  
 Se você vincular a um assembly COM (Assembly A) que se faz referência a outro assembly COM (Assembly B), você também precisa vincular ao Assembly B se uma das seguintes opções for verdadeira:  
  
-   Um tipo do Assembly A herda de um tipo ou implementa uma interface do Assembly B.  
  
-   Um campo, propriedade, evento ou método que possui um tipo de parâmetro ou tipo de retorno do Assembly B é chamado.  
  
 Use [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) para especificar o diretório no qual uma ou mais das suas referências do assembly estão localizado.  
  
 Como o [/Reference](../../../visual-basic/reference/command-line-compiler/reference.md) opção de compilador, o `/link` opção de compilador usa o arquivo de resposta Vbc, que frequentemente usadas referências [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies. Use o [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) opção de compilador se não quiser que o compilador para usar o arquivo Vbc. rsp.  
  
 A forma abreviada do `/link` é `/l`.  
  
## <a name="generics-and-embedded-types"></a>Genéricos e tipos inseridos  
 As seções a seguir descrevem as limitações no uso de tipos genéricos em aplicativos que inserir tipos de interoperabilidade.  
  
### <a name="generic-interfaces"></a>Interfaces genéricas  
 Interfaces genéricas que são inseridos de um assembly de interoperabilidade não podem ser usados. Isso é mostrado no exemplo a seguir.  
  
 [!code-vb[VbLinkCompiler n º&1;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]  
  
### <a name="types-that-have-generic-parameters"></a>Tipos que têm parâmetros genéricos  
 Tipos que têm um parâmetro genérico cujo tipo é incorporado a partir de um assembly de interoperabilidade não podem ser usados se for do tipo de um assembly externo. Essa restrição não se aplicam a interfaces. Por exemplo, considere o <xref:Microsoft.Office.Interop.Excel.Range>interface é definida no <xref:Microsoft.Office.Interop.Excel>assembly.</xref:Microsoft.Office.Interop.Excel> </xref:Microsoft.Office.Interop.Excel.Range> Se uma biblioteca incorpora tipos de interoperabilidade do <xref:Microsoft.Office.Interop.Excel>assembly e expõe um método que retorna um tipo genérico que tem um parâmetro cujo tipo é o <xref:Microsoft.Office.Interop.Excel.Range>da interface, que o método deve retornar uma interface genérica, conforme mostrado no exemplo de código a seguir.</xref:Microsoft.Office.Interop.Excel.Range> </xref:Microsoft.Office.Interop.Excel>  
  
 [!code-vb[VbLinkCompiler n º&2;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]  
[!code-vb[VbLinkCompiler n º&3;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]  
[!code-vb[VbLinkCompiler n º&4;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]  
  
 No exemplo a seguir, o código do cliente pode chamar o método que retorna o <xref:System.Collections.IList>interface genérica sem erro.</xref:System.Collections.IList>  
  
 [!code-vb[VbLinkCompiler n º&5;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila o arquivo de origem `OfficeApp.vb` e fazer referência a assemblies de `COMData1.dll` e `COMData2.dll` para produzir `OfficeApp.exe`.  
  
```vb  
vbc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Passo a passo: Inserindo tipos de Assemblies gerenciados](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)   
 [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)   
 [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Introdução à Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
