---
title: Como criar um arquivo de documentação XML usando CodeDOM
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81d09188ade29b0cac8985da218494f5373980cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397147"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a>Como criar um arquivo de documentação XML usando CodeDOM
O CodeDOM pode ser usado para criar o código que gera a documentação XML. O processo envolve a criação do grafo CodeDOM que contém os comentários de documentação XML, a geração do código e a compilação do código gerado com a opção do compilador que cria a saída de documentação XML.  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a>Para criar um grafo CodeDOM que contém comentários de documentação XML  
  
1.  Crie um <xref:System.CodeDom.CodeCompileUnit> que contém o grafo CodeDOM para o aplicativo de exemplo.  
  
2.  Use o construtor <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> com o parâmetro `docComment` definido como `true` para criar o texto e os elementos de comentário da documentação XML.  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a>Para gerar o código do CodeCompileUnit  
  
1.  Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> para gerar o código e criar um arquivo de origem a ser compilado.  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a>Para compilar o código e gerar o arquivo de documentação  
  
1.  Adicione a opção do compilador **/doc** à propriedade <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> de um objeto <xref:System.CodeDom.Compiler.CompilerParameters> e passe o objeto para o método <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> para criar o arquivo de documentação XML quando o código é compilado.  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir cria um grafo CodeDOM com comentários de documentação, gera um arquivo de código do grafo e compila o arquivo e cria um arquivo de documentação XML associado.  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 O exemplo de código cria a seguinte documentação XML no arquivo HelloWorldDoc.xml.  
  
```xml  
<?xml version="1.0" ?>   
<doc>  
  <assembly>  
    <name>HelloWorld</name>   
  </assembly>  
  <members>  
    <member name="T:Samples.Class1">  
      <summary>  
        Create a Hello World application.   
        <seealso cref="M:Samples.Class1.Main" />   
      </summary>  
    </member>  
    <member name="M:Samples.Class1.Main">  
      <summary>  
        Main method for HelloWorld application.   
        <para>Add a new paragraph to the description.</para>   
      </summary>  
    </member>  
  </members>  
</doc>  
```  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Este exemplo de código requer a permissão `FullTrust` definida para ser executado com êxito.  
  
## <a name="see-also"></a>Consulte também  
 [Documentando o Código com XML](~/docs/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [Comentários da documentação XML](~/docs/csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [Documentação XML](/cpp/ide/xml-documentation-visual-cpp)
