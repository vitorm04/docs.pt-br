---
title: Método ICorDebugProcess6::EnableVirtualModuleSplitting
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
ms.openlocfilehash: 8ad15d11ce81323b30434b3db98259a74a198f29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178567"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>Método ICorDebugProcess6::EnableVirtualModuleSplitting
Habilita ou desabilita a divisão de módulo virtual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `enableSplitting`  
 `true` para habilitar a divisão de módulo virtual; `false` para desabilitá-la.  
  
## <a name="remarks"></a>Comentários  
 A divisão de módulos virtuais faz com que o [ICorDebug](icordebug-interface.md) reconheça módulos que foram mesclados durante o processo de compilação e os apresente como um grupo de módulos separados em vez de um único módulo grande. Fazer isso altera o comportamento de vários métodos [ICorDebug](icordebug-interface.md) descritos abaixo.  
  
> [!NOTE]
> Este método está disponível apenas com .NET Native.  
  
 Esse método pode ser chamado e o valor de `enableSplitting` pode ser alterado a qualquer momento. Ele não causa alterações funcionais imponentes em um objeto [ICorDebug,](icordebug-interface.md) além de alterar o comportamento dos métodos listados na divisão do módulo Virtual e na seção [APIs de depuração não gerenciada](#APIs) no momento em que são chamados. Usar módulos virtuais provoca uma perda de desempenho ao chamar esses métodos. Além disso, o cache significativo na memória dos metadados virtualizados pode ser necessário para implementar corretamente as APIs [IMetaDataImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) e esses caches podem ser retidos mesmo após a divisão de módulos virtuais ter sido desatada.  
  
## <a name="terminology"></a>Terminologia  
 Os seguintes termos são usados para descrever a divisão do módulo virtual:  
  
 módulos de contêiner ou contêineres  
 Os módulos agregados.  
  
 submódulos ou módulos virtuais  
 Os módulos encontrados em um contêiner.  
  
 módulos regulares  
 Módulos que não foram mesclados no tempo de compilação. Eles não são módulos de contêiner nem submódulos.  
  
 Os módulos do contêiner e submódulos são representados por objetos de interface ICorDebugModule. No entanto, o comportamento da interface é \<ligeiramente diferente em cada caso, como descreve a seção x-ref para a seção>.  
  
## <a name="modules-and-assemblies"></a>Módulos e assemblies  
 Vários assemblies de módulo não são suportados para cenários de mesclagem de assembly, portanto, há um relacionamento individual entre um módulo e um assembly. Cada objeto ICorDebugModule, independentemente se ele representa um módulo de contêiner ou um submódulo, possui um objeto ICorDebugAssembly correspondente. O método [ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) converte do módulo para o conjunto. Para mapear na outra direção, o método [ICorDebugAssembly::EnumerateModules](icordebugassembly-enumeratemodules-method.md) enumera apenas 1 módulo. Como o assembly e o module formam um par de ligação estreita nesse caso, os termos assembly e módulo se tornar sinônimos.  
  
## <a name="behavioral-differences"></a>Diferenças de comportamento  
 Módulos de contêiner têm as seguintes características e comportamentos:  
  
- Seus metadados para todos os submódulos constituintes é mesclado.  
  
- Seus nomes de tipos podem ser danificados.  
  
- O método [ICorDebugModule::GetName](icordebugmodule-getname-method.md) retorna o caminho para um módulo on-disk.  
  
- O [método ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) retorna o tamanho dessa imagem.  
  
- O método ICorDebugAssembly3.EnumerateContainedAssemblies lista os submódulos.  
  
- O método ICorDebugAssembly3.GetContainerAssembly retorna `S_FALSE`.  
  
 Submódulos têm as seguintes características e comportamentos:  
  
- Eles têm um conjunto reduzido de metadados que corresponde apenas ao assembly original que foi mesclado.  
  
- Os nomes de metadados não são danificados.  
  
- Os tokens de metadados dificilmente correspondem aos tokens do assembly original antes de ser mesclado no processo de compilação.  
  
- O [método ICorDebugModule::GetName](icordebugmodule-getname-method.md) retorna o nome do conjunto, não um caminho de arquivo.  
  
- O [método ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) retorna o tamanho original da imagem não mesclada.  
  
- O método ICorDebugModule3.EnumerateContainedAssemblies retorna `S_FALSE`.  
  
- O método ICorDebugAssembly3.GetContainerAssembly retorna o módulo recipiente.  
  
## <a name="interfaces-retrieved-from-modules"></a>Interfaces obtidas de módulos  
 Uma variedade de interfaces pode ser criada ou obtida de módulos. Entre eles estão:  
  
- Um objeto ICorDebugClass, que é retornado pelo método [ICorDebugModule::GetClassFromToken](icordebugmodule-getclassfromtoken-method.md) method.  
  
- Um objeto ICorDebugAssembly, que é retornado pelo método [ICorDebugModule::GetAssembly.](icordebugmodule-getassembly-method.md)  
  
 Esses objetos são sempre armazenados em cache pelo [ICorDebug](icordebug-interface.md), e eles terão a mesma identidade de ponteiro, independentemente de terem sido criados ou consultados a partir do módulo de contêiner ou de um submódulo. O submódulo fornece uma exibição filtrada desses objetos em cache, não um cache separado com suas própria cópias.  
  
<a name="APIs"></a>
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Divisão do módulo virtual e APIs de depuração não gerenciadas  
 A tabela a seguir mostra como a divisão de módulo virtual afeta o comportamento de outros métodos na API de depuração não gerenciada.  
  
|Método|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](icordebugfunction-getmodule-method.md)|Retorna o submódulo no qual essa função foi originalmente definida.|Retorna o módulo recipiente ao qual essa função foi mesclada.|  
|[ICorDebugClass::GetModule](icordebugclass-getmodule-method.md)|Retorna o submódulo no qual essa classe foi originalmente definida.|Retorna o módulo recipiente ao qual essa classe foi mesclada.|  
|ICorDebugModuleDebugEvent::GetModule|Retorna o módulo recipiente que foi carregado. Submódulos não recebem eventos de carga independente dessa configuração.|Retorna o módulo recipiente que foi carregado.|  
|[ICorDebugAppDomain::EnumerateAssemblies](icordebugappdomain-enumerateassemblies-method.md)|Retorna uma lista de sub-assemblies e assemblies regulares; nenhum assembly contêiner está incluído. **Nota:**  Se faltar em algum conjunto de contêineres símbolos, nenhum de seus subconjuntos será enumerado. Se qualquer assembly regular estiver com símbolos ausentes, ele pode ou não ser enumerado.|Retorna uma lista de assemblies recipientes e assemblies regulares; nenhum assembly contêiner está incluído. **Nota:**  Se faltar algum conjunto regular, pode ou não ser enumerado.|  
|[ICorDebugCode::GetCode](icordebugcode-getcode-method.md) (ao se referir apenas ao código IL)|Retorna IL que seria válido em uma imagem de assembly pré-mesclagem. Especificamente, qualquer tokens de metadados embutido serão corretamente tokens TypeRef ou MemberRef quando os tipos sendo mencionados não são definidos no módulo virtual que contém o IL. Esses tokens TypeRef ou MemberRef podem ser pesquisados no objeto [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) para o objeto Virtual ICorDebugModule correspondente.|Retorna o IL na imagem de assembly pós-mesclagem.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugProcess6](icordebugprocess6-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
