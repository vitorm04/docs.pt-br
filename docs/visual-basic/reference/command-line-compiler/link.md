---
title: "/link (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Opção de compilador /l [Visual Basic]"
  - "Opção de compilador /link [Visual Basic]"
  - "inserir tipos de interoperabilidade [COM Interop]"
  - "EmbedInteropTypes"
  - "l Opção de compilador [Visual Basic]"
  - "-l Opção de compilador [Visual Basic]"
  - "Opção de compilador link [Visual Basic]"
  - "Opção de compilador -link [Visual Basic]"
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /link (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Faz o compilador manter informações de tipo COM as montagens especificadas disponível para o projeto que você está compilando no momento.  
  
## Sintaxe  
  
```  
/link:fileList  
' -or-  
/l:fileList  
```  
  
## Argumentos  
  
|||  
|-|-|  
|Termo|Definição|  
|`fileList`|Obrigatório.  Lista separada por vírgulas de nomes de arquivo da montagem.  Se o nome do arquivo contiver um espaço, envolva\-o com aspas  \(""\).|  
  
## Comentários  
 O `/link` opção permite que você implanta um aplicativo que incorporou o tipo de informações.  O aplicativo pode usar tipos que implementam as informações de tipo incorporados sem a necessidade de uma referência ao assembly em tempo de execução em um assembly em tempo de execução.  Se forem publicadas várias versões do assembly em tempo de execução, o aplicativo que contém a informação sobre tipos incorporados pode trabalhar com várias versões sem ter que ser recompilado.  Para um exemplo, consulte [Instruções passo a passo: inserindo tipos de assemblies gerenciados](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Usando o `/link` opção é especialmente útil quando você estiver trabalhando com interoperabilidade COM.  Você pode incorporar tipos COM para que o seu aplicativo não requer mais um assembly de interoperabilidade primária \(PIA\) no computador de destino.  O `/link` opção instrui o compilador para incorporar as informações de tipo COM da interop assembly referenciado no código compilado resultante.  O tipo de COM é identificado pelo valor CLSID \(GUID\).  Como resultado, seu aplicativo pode ser executado em um computador de destino que tenha instalado os mesmos tipos de COM os mesmos valores CLSID.  Os aplicativos que automatizam os Microsoft Office são um bom exemplo.  Porque aplicativos como o Office em geral mantêm o mesmo valor CLSID entre diferentes versões, seu aplicativo pode usar os tanto quanto de tipos referenciados COM.NET Framework 4 ou posterior estiver instalado no computador de destino e o seu aplicativo usa métodos, propriedades ou eventos que estão incluídos no referido tipos COM.  
  
 O `/link` opção incorpora apenas interfaces, estruturas e delegados.  Não há suporte para classes COM a incorporação.  
  
> [!NOTE]
>  Quando você cria uma instância de um tipo de COM incorporado no seu código, você deve criar a instância usando a interface adequada.  Tentativa de criar uma instância de um tipo de COM incorporado usando o CoClass causa um erro.  
  
 Para definir o `/link` de opção em [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], adicione uma referência de assembly e definir o `Embed Interop Types` propriedade para  **true**.  O padrão para o `Embed Interop Types` propriedade é  **false**.  
  
 Se você vincular a um assembly COM \(um Assembly\) que por si só faz referência a outro conjunto de COM \(Assembly B\), também é necessário vincular ao Assembly B, se uma das seguintes opções for verdadeira:  
  
-   Um tipo do Assembly A herda de um tipo ou implementa uma interface do Assembly B.  
  
-   Um campo, propriedade, evento ou método que possui um tipo de retorno ou tipo de parâmetro de Assembly B é chamado.  
  
 Use  [\/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) para especificar o diretório no qual uma ou mais das suas referências de assembly estão localizado.  
  
 Como o  [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md) opção de compilador, o `/link` opção de compilador usa o arquivo de resposta do Vbc. rsp, as referências usadas com freqüência [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies.  Use o  [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) opção de compilador, se você não quiser que o compilador para usar o arquivo VBC. rsp.  
  
 A forma abreviada do `/link` é `/l`.  
  
## Genéricos e tipos incorporados  
 As seções a seguir descrevem as limitações no uso de tipos genéricos em aplicativos que incorporam os tipos de interoperabilidade.  
  
### Interfaces Genéricas  
 Interfaces genéricas que são incorporados a partir de um assembly de interoperabilidade não podem ser usados.  Isto é mostrado no exemplo a seguir.  
  
 [!code-vb[VbLinkCompiler#1](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]  
  
### Tipos que possuem parâmetros genéricos  
 Tipos que têm um parâmetro genérico cujo tipo é incorporado a partir de um assembly de interoperabilidade não podem ser usados se que seja do tipo de um assembly externo.  Essa restrição não se aplica às interfaces.  Por exemplo, considere a <xref:Microsoft.Office.Interop.Excel.Range> interface é definida na <xref:Microsoft.Office.Interop.Excel> assembly.  Se uma biblioteca incorpora os tipos de interoperabilidade da <xref:Microsoft.Office.Interop.Excel> assembly e expõe um método que retorna um tipo genérico que tem um parâmetro cujo tipo é o <xref:Microsoft.Office.Interop.Excel.Range> de interface, que o método deve retornar uma interface genérica, conforme mostrado no exemplo de código a seguir.  
  
 [!code-vb[VbLinkCompiler#2](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]  
[!code-vb[VbLinkCompiler#3](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]  
[!code-vb[VbLinkCompiler#4](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]  
  
 No exemplo a seguir, o código do cliente pode chamar o método que retorna o <xref:System.Collections.IList> interface genérica sem erro.  
  
 [!code-vb[VbLinkCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]  
  
## Exemplo  
 O código a seguir compila o arquivo de origem `OfficeApp.vb` e assemblies de referência `COMData1.dll` e `COMData2.dll` para produzir `OfficeApp.exe`.  
  
```vb#  
vbc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Instruções passo a passo: inserindo tipos de assemblies gerenciados](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [\/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)   
 [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Introdução à interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)