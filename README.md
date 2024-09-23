# HyperLaneSuperBridge


### 0. 시작하기 전 

#### 네트워크 고르기
[수퍼브릿지](https://superbridge.app/)

여기에서 지원하는 네트워크 두가지 골라주세여. 

**두가지 체인에 모두 ETH소량 필요함 (1$쯤? 나중에 정확히 알려줌 근데 실제로 사용은 그것만큼도 안함)**


#### 토큰 고르기
토큰은 원하는거 정하세요.

출발하는 네트워크의 토큰 어드레스 미리 찾아두기.

(베이스 네트워크의 디젠인경우, 
![image](https://github.com/user-attachments/assets/6d52e0b1-7680-40fa-808c-654ec4745da9)
![image](https://github.com/user-attachments/assets/cafcfef9-1dc2-4790-a4ac-f4b06ff47cbe)
미리 복사해두기)

#### 지갑의 프빗키
메인지갑말고 다른거로 쓰는게 좋을듯.

![image](https://github.com/user-attachments/assets/0e568dbd-6162-4e44-8310-f61d41bfa2ab)
![image](https://github.com/user-attachments/assets/5f737516-f62b-4037-be91-7143d3315f53)

복사해두기.

저는 예시로 Base의 Degen을 ZoraMainnet으로 옮기는 브릿지를 만들어볼게요.

### 1. 설치

#### 도커
```
curl -fsSL https://fnm.vercel.app/install | bash
source ~/.bashrc
fnm use --install-if-missing 20
```

#### 하이퍼레인 툴
```
npm install -g @hyperlane-xyz/cli
```

### 2. 지갑설정


```
export HYP_KEY=프빗키
```

프빗키부분을 미리 저장해둔 실제 키로 바꾸세효.
(예 : export HYP_KEY=1a2s1c5cz4...)



### 3. Config 만들기

```
hyperlane warp init
```

![image](https://github.com/user-attachments/assets/3bec3975-1547-4073-8f1b-c5bb43c1f1b8)

빨간에러는 그냥 무시하면되긔. 지갑주소 맞나 확인하고 Y    
다음 Mainnet 엔터

![image](https://github.com/user-attachments/assets/805c1757-62c6-4067-a595-df702835052e)

여기서 아까 정한 두가지 네트워크를 선택해야합니긔. 방향키 위아래로 움직이고 (계속 움직이면 페이지 넘어감) 스페이스바로 선택.    
두개다 선택하면 엔터 눌르세효.

(예 : ![image](https://github.com/user-attachments/assets/ac024800-6192-44f1-a07e-79941769b555)



Base와 ZoraMainnet를 고른모습)

다음, 토큰의 타입 정하기. 똑같이 방향키로 정하고 엔터누르면 넘어가요.    

![image](https://github.com/user-attachments/assets/2ab1b3de-abec-4334-808f-866cb804a47f)

**ETH일경우 Native, 아닐경우 '출발하는 네트워크'는 Collateral**    
**'도착하는 네트워크'는 Synthetic.**    
예시의 경우 'base'의 토큰 타입을 물어보니까 Collateral, 엔터.

![image](https://github.com/user-attachments/assets/58b85936-ac73-4981-8493-111ab8d6ef90)
이건 그냥 Y엔터


![image](https://github.com/user-attachments/assets/d7f39475-375a-4293-9cc7-37ee8eb49795)    
'출발하는 네트워크'의 '토큰 주소'를 묻고있어요.    
예시로 Base 네트워크의 Degen주소를 넣을게효.
![image](https://github.com/user-attachments/assets/c8a632ae-7f2e-4537-a18a-22ee5717d6b7)    
토큰주소 붙여넣고 엔터.

![image](https://github.com/user-attachments/assets/da342ca4-f633-447c-8a1a-30529d350ae7)    
이번엔 ZoraMainnet의 토큰타입을 묻습니다.    
Synthetic, 엔터.

![image](https://github.com/user-attachments/assets/b5f69262-2bad-4184-a3d2-db6b09ad6614)    
똑같이 Y, 엔터


![image](https://github.com/user-attachments/assets/17f199e5-1215-4636-8e8d-04578d3c1556)    
완! 문서가 만들어집니다.


    
    
    
    


### 4. 브릿지 만들기.
```
hyperlane warp deploy
```

![image](https://github.com/user-attachments/assets/5774dbe0-816e-45d3-b649-d7bf874c9994)    
두번 묻는데 둘다 N, 엔터
![image](https://github.com/user-attachments/assets/635ea4e7-e722-44e7-9764-be98fc0092d7)    
Y, 엔터

![image](https://github.com/user-attachments/assets/b112f8d1-5d43-4309-890a-350551e1a28c)

**필요한 ETH를 알려줍니다. 지갑에 충전한다음 Y 엔터**

![image](https://github.com/user-attachments/assets/21c4cb68-9444-4ab9-8445-a20d3ca8f504)

기다리시긔.. 몇분걸림. 만약 실패했다면 4단계부터만 다시 하면됨!!

![image](https://github.com/user-attachments/assets/9075f42b-4d48-4ed9-8fe3-a61156269a9d)    
완!! 가스비 사용한거보면 사실 얼마안쓴것도 보임.    



**이제 여기서 잘따라하세효.**    
![image](https://github.com/user-attachments/assets/fa809684-f6f8-4b9c-8892-3dca2b2b61d8)    
**이렇게 블록지정을하고(드래그) 마우스 우클릭. 그럼 복사됩니다. 메모장에 저장해두기.**




### 5. 수퍼브릿지 만들기.
[커스텀 수퍼브릿지](https://hyperlane.superbridge.app/)

![image](https://github.com/user-attachments/assets/8c323e9e-cd0f-4bbf-bdec-0038e6ce69f2)

![image](https://github.com/user-attachments/assets/f32674ac-962d-4191-8742-57c2c249e85d)

![image](https://github.com/user-attachments/assets/ea35a80f-9e3e-41ce-8247-3c89ba8a2c0e)    
아까 메모장에 복사해둔거 그대로 붙여넣고 Save.     
기다리면 주소도 바뀌고, 네트워크 From, To눌러보면 여러분이 설정한 네트워크가 추가되어있어요!!!~

![image](https://github.com/user-attachments/assets/826cad16-990a-4b8e-a81d-718cd8a9bf90)

지갑연결하고 토큰을 소량씩 여러번 보내보시긔.    
주소는 즐겨찾기 해둬도?? 될듯??    
**끝**



