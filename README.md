# test

package com.Rococo.auth_id_app;

import android.content.Context;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;
import android.graphics.Path;
import android.util.AttributeSet;
import android.view.View;


public class MyView extends View {
    private final Paint paint = new Paint();
    //private final Path path = new Path();
    private int yval;

    public int[] ltrb = new int[4];
    public int[] color = new int[4];

    public MyView(Context context, AttributeSet attrs) {
        super(context, attrs);
        yval = 450;
        ltrb[0] = 0;
        ltrb[1] = 0;
        ltrb[2] = 0;
        ltrb[3] = 0;
    }

    public void setPositon(int left,int top,int right,int bottom) {
        ltrb[0] = left;
        ltrb[1] = top;
        ltrb[2] = right;
        ltrb[3] = bottom;
    }
    public void setColor(int alpha,int red,int green,int blue) {
        color[0] = alpha;
        color[1] = red;
        color[2] = green;
        color[3] = blue;
    }

    @Override
    protected void onDraw(Canvas canvas) {
        // 背景、半透明
        canvas.drawColor(Color.argb(0, 0, 0, 0));

        // 矩形
        paint.setColor(Color.argb(color[0], color[1], color[2], color[3]));
        paint.setStrokeWidth(7);
        paint.setStyle(Paint.Style.STROKE);
        // (x1,y1,x2,y2,paint) 左上の座標(x1,y1), 右下の座標(x2,y2)
        canvas.drawRect(ltrb[0],ltrb[1],ltrb[2],ltrb[3],paint);

    }
}

＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿＿
    public void moveCircle(int left,int top,int right,int bottom){
        runnable = new Runnable() {
            @Override
            public void run() {
                if(flg == 1){
                    //pos += 10;
                    myView.setPositon(ltrb[0],ltrb[1],ltrb[2],ltrb[3]);
                    myView.setColor(255,0,255,0);
                    myView.invalidate();
                    myView.bringToFront();
                    handler.postDelayed(this, 100);
                }
                else if (flg == 2){
                    myView.setPositon(ltrb[0],ltrb[1],ltrb[2],ltrb[3]);
                    myView.setColor(255,255,0,0);
                    myView.invalidate();
                    myView.bringToFront();
                    handler.postDelayed(this, 100);
                }
                else{

                }
            }
        };
        handler.post(runnable);
    }
    
    _________________________________________________________________________________
                // Draw rectangle for detected face
            RFAFace fvFace = faces.get(0);
            Rect rect = fvFace.getBounds();
            ltrb[0] = rect.x;
            ltrb[1] = rect.y;
            ltrb[2] = rect.x + rect.width;
            ltrb[3] = rect.y + rect.height;

            Resources r = getResources();
            float cameraPreviewWidth = TypedValue.applyDimension(
                    TypedValue.COMPLEX_UNIT_DIP, 190,
                    r.getDisplayMetrics()
            );
            //System.out.println(cameraPreviewWidth);
            float multiplier = 2;//(cameraPreviewWidth/parameters.getPreviewSize().height);

            ltrb[0] = (int)(ltrb[0] * multiplier);
            ltrb[1] = (int)(ltrb[1] * multiplier);
            ltrb[2] = (int)(ltrb[2] * multiplier);
            ltrb[3] = (int)(ltrb[3] * multiplier);

            moveCircle(ltrb[0], ltrb[1], ltrb[2], ltrb[3]);
            System.out.println("Rectを生成");
