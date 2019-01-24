---
title: Exemplo de tecnologia de serialização básica
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: 43e69ce90b86053badad91b62ec288378e63e2ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681697"
---
# <a name="basic-serialization-technology-sample"></a>Exemplo de tecnologia de serialização básica
[Baixar exemplo](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 Esse exemplo demonstra a habilidade do common language runtime de serializar um grafo de objeto na memória para um fluxo. Esse exemplo pode usar o <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ou o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> para serialização. Uma lista vinculada, preenchida com dados, é serializada ou desserializada para ou de um fluxo de arquivos. Em ambos os casos, a lista é exibida para que você possa ver os resultados. A lista vinculada é do tipo `LinkedList`, um tipo definido por essa amostra.  
  
 Revise os comentários no código de origem e nos arquivos build.proj para obter mais informações sobre serialização.  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>Para criar o exemplo usando o Prompt de Comando  
  
1.  Navegue para um dos subdiretórios específicos da linguagem no diretório Technologies\Serialization\Runtime Serialization\Basic directory, usando o prompt de comando.  
  
2.  Digite **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** ou **msbuild SerializationVB.sln**, dependendo de sua escolha da linguagem de programação, na linha de comando.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Para criar o exemplo usando Visual Studio  
  
1.  Abra o [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] e navegue para um dos subdiretórios específicos da linguagem para o exemplo.  
  
2.  Clique duas vezes no ícone para o arquivo SerializationCS.sln, SerializationJSL.sln ou SerializationVB.sln, dependendo de sua escolha da linguagem de programação para abrir o arquivo no Visual Studio.  
  
3.  No menu **Compilar**, selecione **Compilar Solução**.  
  
 O aplicativo de exemplo será criado no subdiretório padrão \bin ou \bin\Debug.  
  
### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Navegue para o diretório contendo o executável compilado.  
  
2.  Digite **Serialization.exe**, junto com os valores de parâmetro desejados, na linha de comando.  
  
    > [!NOTE]
    >  Esse exemplo cria um aplicativo de console. Você deve lançá-lo usando o prompt de comando para exibir a saída.  
  
## <a name="remarks"></a>Comentários  
 O aplicativo de exemplo aceita parâmetros da linha de comando indicando qual teste você gostaria de executar. Para serializar uma lista de 10 nós para um arquivo chamado **Test.xml** usando o formatador SOAP, use os parâmetros **sx Test.xml 10**.  
  
 Por exemplo:  
  
 **Serialize.exe -sx Test.xml 10**  
  
 Para desserializar o arquivo **Test.xml** do exemplo anterior, use os parâmetros **dx Test.xml**.  
  
 Por exemplo:  
  
 **Serialize.exe -dx Test.xml**  
  
 Nos dois exemplos acima, o "x" na opção de linha de comando indica que você quer a serialização SOAP de XML. Você pode usar "b" nesse local para usar a serialização binária. Se você quiser tentar a serialização com um número muito grande de nós, pode querer redirecionar a saída do console para um arquivo.  
  
 Por exemplo:  
  
 **Serialize.exe -sb Test.bin 10000 >somefile.txt**  
  
 Os seguintes marcadores descrevem brevemente as classes e as tecnologias usadas por esse exemplo.  
  
-   Serialização em tempo de execução  
  
    -   <xref:System.Runtime.Serialization.IFormatter> Usado para referir-se a um objeto <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ou <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Usado para serializar uma lista vinculada a um fluxo em um formato binário. O formatador binário usa um formato que somente o tipo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> entende. No entanto, os dados são concisos.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Usado para serializar uma lista vinculada a um fluxo no formato SOAP. SOAP é um formato padrão.  
  
-   E/S de fluxo  
  
    -   <xref:System.IO.Stream> Usado para serializar e desserializar. O tipo de fluxo específico usado nesse exemplo é o tipo <xref:System.IO.FileStream>. No entanto, a serialização pode ser usada com qualquer tipo derivado de <xref:System.IO.Stream>.  
  
    -   <xref:System.IO.File> Usado para criar objetos <xref:System.IO.FileStream> para ler e criar arquivos em disco.  
  
    -   <xref:System.IO.FileStream> Usado para serializar e desserializar listas vinculadas.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IO>
- <xref:System.IO.File>
- <xref:System.IO.FileStream>
- <xref:System.IO.Stream>
- <xref:System.Random>
- <xref:System.Runtime.Serialization>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.IFormatter>
- <xref:System.SerializableAttribute>
- <xref:System.Xml.Serialization>
- [Serialização básica](../../../docs/standard/serialization/basic-serialization.md)
- [Serialização binária](../../../docs/standard/serialization/binary-serialization.md)
- [Controlando a serialização XML usando atributos](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)
- [Apresentando a serialização XML](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [Serialização](../../../docs/standard/serialization/index.md)
- [Serialização XML e SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)
