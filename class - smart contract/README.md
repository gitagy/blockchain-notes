
컴퓨터 과학자인 Nick Szabo는 1993년 Smart Contract라는 컴퓨터 프로토콜의 한 형태를 발표

특성
자가 실행이 가능하여야 하고, 부분적, 또는 전체적으로 실행

Smart Contract를 구현하는 Blockchain 플렛폼은 Ethereum만 있는 것이 아닙니다. Linux Foundation과 30개의 다국적 기업이 참여한 HyperLedger 또한 Smart Contract 구현체입니다. 현제 참여한 회사들이 구현체를 각각 만들고 있으며, 아직 어느것하나 컨셉증명을 넘어서진 않았습니다.



https://winterj.me/realistic-smart-contract/

외부 연동
 * Oraclize와 투표자를 둬서 상호 검증할 수 있게끔 활용하는 방법을 생각해 볼 수 있겠다. Oraclize는 현재 컨트랙트에서 외부 데이터를 제공받을 수 있는 사실상 표준 기술이며 이를 활용하는 것이 효율적이다.

 * 여러가지 이유로 Oraclize가 동작하지 않을 때 컨트랙트가 제대로 작동하지 않을 때가 있을 수 있다. 이럴 경우를 대비해 Oraclize관련 처리 루틴을 fetch부분과 process부분으로 분리해 두고, Oraclize가 다운 등의 이유로 동작하지 않을 땐 process부분에 필요한 정보를 직접적으로 입력해준다. 즉각적으로 실행하는 대신 잠시 지연시켜두고 사용자의 검증을 받을 수 있게 한다. 컨트랙트 서비스 제공 업자측에서 이를 공시해 사용자에게 유효성 검증을 받는다. 사용자는 예치금과 함께 정보의 타당성을 검증하며 다수의 사용자가 승인할 때만 실질적인 처리가 이루어 지도록 할 수 있다. 추후 Oraclize가 복구되었을 때 이를 다시 한 번 검증해 부정 검증이었을 경우 예치금을 몰수하며 올바른 검증이었을 경우엔 업자측에서 보상을 주는 방법으로 보완하는 방법도 생각해 볼 수 있다.



계약의 신뢰와 검증
 * 일반적인 경우 한번 blockchian에 deploy된 smart contract의 경우 코드 및 contract를 수정할 수 없다. 하지만 언제든 뒤늦게 contract에서 에러가 발견되거나 기타 이유로 로직 변경, 추가가 필요할 수 있다. 이 같은 상황에 시도할 수 있는 최선의 방안


계약 내용 고치기
 * 그 보다 좀 더 컨트랙트 중심의 로직을 활용하고 싶으면 디스패처-로직-스토리지 컨트랙트로 분리해 활용할 수도 있다. 디스패처는 최신 스마트 컨트랙트 주소를 가리키며 업데이트 가능하다. 디스패처와 로직간에는 delegatecall로 데이터를 전달하고 함수를 실행해 반환값을 돌려받는다. 저장되어 있는 데이터 또한 보존되어야 하므로 별도의 컨트랙트로 분리한다.
 * 다만 갱신 가능한 스마트 컨트랙트를 사용한다면 결국 업자가 스마트 컨트랙트의 내용을 마음대로 변경할 수 있음을 뜻한다. 이는 신뢰 문제에 있어서 결국 사용자는 업자가 블록체인과 스마트 컨트렉트를 쓰든 쓰지않든 똑같이 업자를 믿고 갈 수 밖에 없다. 이런 상황에서 굳이 갱신 가능한 스마트 컨트랙트에 여러 기능을 넣어 구축하기 보다는 robust한 코어 로직을 스마트 컨트랙트를 토대로 운영하고 그 외에는 중앙화된 신뢰할 수 있는 서비스 제공 업자가 처리하거나 일반 사용자들에게 투표를 받아 일정 비율 이상이면 갱신 가능하게 만드는게 더 좋을 것이라 생각한다.




이더리움
 - 언어
 EVM
 solidity
 bytecode
 ABI
 state
 call



간단히 뭘 하나 만들어 보즈아...



EOS
 - 언어

Tezos
 - 언어

HyperLedger


https://github.com/HomoEfficio/warehouse/blob/master/etc/Ethereum-dApp-%EA%B0%9C%EB%B0%9C.md
