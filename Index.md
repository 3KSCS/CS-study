Index는 책의 북마크와 같다.
Index를 사용하지 않는 테이블은 처음부터 끝까지 검색하는 방법인 FTS(Full Table Scan)을 사용하는데
Index를 사용하면 바로 Index로 찾아가서 거기서만 찾기 때문에 더 빠르게 검색이 가능하다.

예를들어, DB를 책으로 비유하면 데이터는 책의 내용일 것이고, 데이터가 저장된 레코드의 주소는 index 목록에 있는 페이지 번호일 것이다.

인덱스는 항상 정렬된 상태를 유지하기 때문에 원하는 값을 검색하는데 빠르지만,
새로운 값을 추가하거나 삭제, 수정하는 경우에는 쿼리문 실행 속도가 느려진다.

즉, 인덱스는 검색 속도를 높이는 기능이지만, DB에 값이 변경되는 성능은 떨어진다.