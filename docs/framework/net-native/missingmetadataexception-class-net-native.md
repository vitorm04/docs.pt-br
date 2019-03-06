---
title: Classe MissingMetadataException (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: 408f25c4-6d60-475c-92b1-7b52b777c6db
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2961a4c02d8ffe17055307094f56a03680d1a59a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357125"
---
# <a name="missingmetadataexception-class-net-native"></a>Classe MissingMetadataException (.NET Nativo)

**.NET para Aplicativos da Windows Store para Windows 10, somente [!INCLUDE[net_native](../../../includes/net-native-md.md)]**

A exceção que é acionada quando reflexão é usada para recuperar metadados não presentes.

**Namespace:** System.Reflection

> [!IMPORTANT]
> A classe `MissingMetadataException` destina-se somente para uso interno da cadeia de ferramentas [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Ela não é destinado para uso em código de terceiros e você também não deve tratar a exceção no seu código do aplicativo. Em vez disso, elimine a exceção adicionando entradas ao seu [arquivo de diretivas de tempo de execução](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Para obter mais informações, consulte a seção Comentários.

## <a name="syntax"></a>Sintaxe

[!code-csharp[ProjectN#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingmetadataexception_syntax1.cs#4)]

Observe que a classe `MissingMetadataException` deriva de <xref:System.TypeAccessException>.

A classe `MissingMetadataException` tem os seguintes membros:

## <a name="constructors"></a>Construtores

|Construtor|Descrição|
|-----------------|-----------------|
|`public MissingMetadataException()`|Inicializa uma nova instância da classe `MissingMetadataException` usando uma mensagem fornecida pelo sistema que descreve o erro.<br /><br /> Esse construtor destina-se ao uso interno somente pela cadeia de ferramentas [!INCLUDE[net_native](../../../includes/net-native-md.md)].|
|`public MissingMetadataException(String message)`|Inicializa uma nova instância da classe `MissingMetadataException` com uma mensagem de erro especificada.<br /><br /> Esse construtor destina-se ao uso interno somente pela cadeia de ferramentas [!INCLUDE[net_native](../../../includes/net-native-md.md)].|

## <a name="properties"></a>Propriedades

|Propriedade|Descrição|
|--------------|-----------------|
|`public IDictionary Data { get; }`|Obtém uma coleção de pares de chave/valor que fornecem informações adicionais definidas pelo usuário sobre a exceção. (Herdado de <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string HelpLink { get; set; }`|Obtém ou define um link para o arquivo de ajuda associado a essa exceção. (Herdado de <xref:System.Exception?displayProperty=nameWithType>.)|
|`public int HResult { get; protected set; }`|Obtém ou define o `HRESULT`, um valor numérico codificado que é atribuído a uma exceção específica. (Herdado de <xref:System.Exception?displayProperty=nameWithType>.)|
|`public Exception InnerException { get; }`|Obtém a exceção que causou a exceção atual. (Herdado de <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string Message { get; }`|Obtém uma mensagem que descreve a exceção atual. (Herdado de <xref:System.TypeLoadException>.)|
|`public string Source { get; set; }`|Obtém ou define o nome do aplicativo ou objeto que causou o erro. (Herdado de <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string StackTrace { get; }`|Obtém uma representação de cadeia de caracteres de quadros imediatos na pilha de chamadas. (Herdado de <xref:System.Exception?displayProperty=nameWithType>.)|
|`public MethodBase TargetSite { get; }`|Obtém o método que acionou a exceção atual. (Herdado de <xref:System.Exception?displayProperty=nameWithType>.)|
|`public string TypeName { get; ]`|Obtém o nome totalmente qualificado do tipo cujos metadados estão ausentes. (Herdado de <xref:System.TypeLoadException>.)|

## <a name="methods"></a>Métodos

|Método|Descrição|
|------------|-----------------|
|`public bool Equals(Object obj)`|Determina se o objeto especificado é igual ao objeto atual.  (Herdado de <xref:System.Exception?displayProperty=nameWithType>.)|
|`protected void Finalize()`|Permite que um objeto tente liberar recursos e executar outras operações de limpeza antes de ser recuperado pela coleta de lixo. (Herdado de <xref:System.Object>.)|
|`public Exception GetBaseException()`|Retorna a exceção é a causa raiz de uma ou mais exceções subsequentes. (Herdado de <xref:System.Exception?displayProperty=nameWithType>.)|
|`public int GetHashCode()`|Retorna um código de hash para uma instância `MissingMetadataException`.   (Herdado de <xref:System.Object>.)|
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Define um objeto <xref:System.Runtime.Serialization.SerializationInfo> com informações sobre a exceção.  (Herdado de <xref:System.TypeLoadException>.)|
|`public Type GetType()`|Obtém o tipo de tempo de execução da instância atual. (Herdado de <xref:System.Exception?displayProperty=nameWithType>.)|
|`protected Object MemberwiseClone()`|Cria uma cópia superficial do objeto atual. (Herdado de <xref:System.Object>.)|
|`public string ToString()`|Retorna a representação de cadeia de caracteres de exceção atual. (Herdado de <xref:System.Exception?displayProperty=nameWithType>.)|

## <a name="events"></a>Eventos

|Evento|Descrição|
|-----------|-----------------|
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Ocorre quando uma exceção é serializada para criar um objeto de estado de exceção que contém dados serializados sobre a exceção. (Herdado de <xref:System.Exception?displayProperty=nameWithType>.)|

## <a name="usage-details"></a>Detalhes de uso

A exceção `MissingMetadataException` é acionada quando a reflexão é usada para acessar os metadados não disponíveis em um assembly.

Os metadados disponíveis em um aplicativo no tempo de execução é definido pelo arquivo de diretivas (configuração XML) de tempo de execução, *. rd.xml. Para impedir que o seu aplicativo acione esta exceção, você deve modificar o \*.rd.xml para definir os metadados que devem estar presentes no tempo de execução. Para obter informações sobre o formato do arquivo \*.rd.xml, consulte [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).

> [!IMPORTANT]
> Como essa exceção indica que os metadados exigidos pelo seu aplicativo não estão disponíveis no tempo de execução, você não deve tratar essa exceção em um bloco `try`/`catch`. Em vez disso, você deve diagnosticar a causa da exceção e eliminá-la usando um arquivo de diretivas de tempo de execução. Para obter a entrada que você pode adicionar ao seu arquivo de diretivas de tempo de execução e que elimina a exceção, você pode usar uma das duas soluções de problemas:
>
> - A [solução de problemas MissingMetadataException](https://dotnet.github.io/native/troubleshooter/type.html) para tipos.
> - A [solução de problemas MissingMetadataException](https://dotnet.github.io/native/troubleshooter/method.html) para métodos.

A classe `MissingMetadataException` não contém membros exclusivos. Todos os seus membros são herdados de sua classe base, <xref:System.TypeAccessException>.

## <a name="see-also"></a>Consulte também

- <xref:System.Exception?displayProperty=nameWithType>
- <xref:System.TypeAccessException>
- [Classe MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)
- [Classe MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)
- [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
