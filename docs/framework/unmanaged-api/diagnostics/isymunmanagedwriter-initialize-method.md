---
title: ISymUnmanagedWriter::Initialize (Método)
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44046560f4f788c4a7d695ff18c9c01740fea35a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriterinitialize-method"></a>ISymUnmanagedWriter::Initialize (Método)
Establece la interfaz emisora de metadatos con el que se asociará este sistema de escritura y el nombre de archivo de salida a la que se escribirán los símbolos de depuración.  
  
 Puede llamar a este método solo una vez y debe llamarse antes de cualquier otro método de escritura. Algunos escritores pueden requerir un nombre de archivo. Sin embargo, siempre se puede pasar un nombre de archivo a este método sin ningún efecto negativo en escritura que no utilicen el nombre de archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `emitter`  
 [in] Un puntero a interfaz emisora de metadatos.  
  
 `filename`  
 [in] El nombre de archivo a la que se escriben los símbolos de depuración. Si se especifica un nombre de archivo para un escritor que no usa nombres de archivo, se omite este parámetro.  
  
 `pIStream`  
 [in] Si se especifica, el escritor de símbolos emitirá los símbolos en el dado <xref:System.Runtime.InteropServices.ComTypes.IStream> en vez de en el archivo especificado en el `filename` parámetro. El parámetro `pIStream` es opcional.  
  
 `fFullBuild`  
 [in] `true` si se trata de una regeneración completa; `false` si se trata de una compilación incremental.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si el método tiene éxito; en caso contrario, E_FAIL u otro código de error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Vea también  
 [ISymUnmanagedWriter (interfaz)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Initialize2 (método)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
