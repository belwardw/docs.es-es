---
title: "ISymUnmanagedScope2::GetConstantCount (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope2.GetConstantCount
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 26ce28c3542af80f033cc765c3e462a34e4fb3e4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="ed357-102">ISymUnmanagedScope2::GetConstantCount (Método)</span><span class="sxs-lookup"><span data-stu-id="ed357-102">ISymUnmanagedScope2::GetConstantCount Method</span></span>
<span data-ttu-id="ed357-103">Obtiene un recuento de las constantes definidas dentro de este ámbito.</span><span class="sxs-lookup"><span data-stu-id="ed357-103">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed357-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ed357-104">Syntax</span></span>  
  
```  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed357-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ed357-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ed357-106">[out] Un puntero a un `ULONG32` que recibe el tamaño, en caracteres, del búfer necesario para contener las constantes.</span><span class="sxs-lookup"><span data-stu-id="ed357-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed357-107">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="ed357-107">Return Value</span></span>  
 <span data-ttu-id="ed357-108">S_OK si el método tiene éxito; en caso contrario, E_FAIL u otro código de error.</span><span class="sxs-lookup"><span data-stu-id="ed357-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed357-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ed357-109">Requirements</span></span>  
 <span data-ttu-id="ed357-110">**Encabezado:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ed357-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed357-111">Vea también</span><span class="sxs-lookup"><span data-stu-id="ed357-111">See Also</span></span>  
 [<span data-ttu-id="ed357-112">ISymUnmanagedScope2 (interfaz)</span><span class="sxs-lookup"><span data-stu-id="ed357-112">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)