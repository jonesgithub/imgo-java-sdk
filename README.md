# imgo-java-sdk
java sdk for imgo

# Usage

``` java
String pushAddress = "127.0.0.1:8080";
String token = "abcdefg123456789";
//use sdk to connect imgo
try{
    PushClient client = new PushClient(pushAddress,token);
    client.setClientEventListener(new ClientEventListener() {
        @Override
        public void onConnectionStateChanged(ConnectionState currentState) {
            System.out.println("current state is "+ currentState.name());
        }

        @Override
        public void onError(Exception e) {
            System.out.println("error："+e.getMessage());
        }

        @Override
        public void onAuth(boolean success) {
            System.out.println("auth："+success);
        }

        @Override
        public void onMessage(long version, String message) {
            System.out.Println("version:"+version+",msg:"+message);
        }
    });
    client.start();
}catch (Exception e){
    System.out.println("fetal："+e.getMessage());
}

```

