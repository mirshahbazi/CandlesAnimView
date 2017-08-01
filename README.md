# CandlesAnimView
---
&emsp;&emsp;The design idea comes from Gal Shir's GIF design, the right candle blows out the left side of the candle, and constantly circulates as a move, joined the interface to stop the animation, but temporarily did not want to end the animation in what form should show more natural, the current animation End to stop candles

# DEMO
---
![](https://github.com/Yellow5A5/CandlesAnimView/blob/master/demo.gif)

# Structure
---
![](https://github.com/Yellow5A5/CandlesAnimView/blob/master/structure.png)

# API
---
&emsp;&emsp;Temporarily only wrote the end of the animation interface, but also joined the candle action callback, if necessary, can expand their own other aspects of the effect。

```
    //Listen to the end of the animation
    private StopAnimListener mStopAnimListener;

    public interface StopAnimListener{
        //End the animation call after the method is started
        public void OnAnimStop();
    }

    public void setStopAnimListener(StopAnimListener l){
        this.mStopAnimListener = l;
    }
```

```
    /*
     Call the end of the animation
     */
    public void stopAnim(){
        mAnimControler.stopAnimation();
        if(mStopAnimListener != null){
            mStopAnimListener.OnAnimStop();
        }
    }
```

```
        mCandlesAnimView.setStopAnimListener(new CandlesAnimView.StopAnimListener() {
            @Override
            public void OnAnimStop() {
                Toast.makeText(MainActivity.this,"End Anim.",Toast.LENGTH_SHORT).show();
            }
        });
```

# Call the way
---
 1. Configure XML

```
    <com.yellow5a5.candlesanimlib.CandlesAnimView
        android:id="@+id/candles_view"
        android:layout_centerInParent="true"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />
```

 2. Java code created
```
        CandlesAnimView mCandlesAnimView = new CandlesAnimView(MainActivity.this);
        //...addView..
```

# other
---
&emsp;&emsp;The current animation ends for the stop blowout candles. Adaptation through the View itself by the ratio of the width of the set is not ideal, you can modify the fixed mHeight and mWidth internal logic perfect.

#Change

&emsp;&emsp;By Mohammad ALi Mir Shahbazi (MAM)
